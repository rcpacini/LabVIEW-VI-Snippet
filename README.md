# LabVIEW-VI-Snippet
VI Snippet (.png) Import and Export Library for LabVIEW

Import or export a VI Snippet (.png) image programmatically using pure
LabVIEW code (No external dlls or dependencies).

## Getting Started

Refer to the `/Examples/Example.vi` to Import or Export a VI Snippet image.

![VI-Snippet Example](/Demo.png)

![VI-Snippet Sample](/Help/Sample.png)

## What's a VI Snippet?
[VI Snippets](http://www.ni.com/tutorial/9330/en/) are PNG image (.png)
embedded with LabVIEW code to solve the copy-and-paste (or drag-and-drop)
dilemma with graphical programming. Introduced in 2014, VI Snippets provide
a human readable view of code fragments, similar to what you see on
stack exchange, that can be imported into the LabVIEW Development
Environment.

VI Snippet images (like the one below) are dropped onto a VI's Block
Diagram to copy the code snippet into the LabVIEW environment.

![Basic VI Snippet](/Examples/Snippets/basic.png)

Over 9 years have passed and NI has yet to include an
[VI Snippet API](http://www.ni.com/tutorial/9330/en/)
so I built one myself...

## Features
In addition to supporting the basic VI Snippet drag-and-drop capabilities,
this library can also:
- Copy Front Panel objects to their original positions
- Wire the connector pane terminals
- Update the VI Icon
- Clone the VI Properties

## Additional Information
VI Snippets are no more than PNG files with a custom PNG chunk
type called `niVI` which embed the binary VI.

*Note: This library uses VI Scripting to make a selection of all block diagram
objects (i.e. decorations, nodes, sub VIs, wires, etc.) and copies the
GObjects to the clipboard in the context of the block diagram.
This is a workaround due to the inconsistent nature of the
"Place object on cursor" IDE method.*

### VI Snippet PNG Chunks

| Type | Description |
| --- | --- |
| `IHDR` | PNG header information |
| `IDAT` | PNG image data |
| **`niVI`** | **LabVIEW VI code** << this is the secret sauce<br>E.g. `RSRC...VI_NAME.vi` |
| **`tEXt`** | **LabVIEW VI Snippet help text**<br>E.g. `National Instruments Software This image contains an embedded VI File. For more details visit ni.com/info and enter 'ex6a7h'` |
| `IEND` | PNG end of file |

## Build
To rebuilt the VI Snippet Packed Library, open the `VI-Snippet.lvproj`,
right-click the `VI-Snippet` packed library and select **Build**.

The Packed Library (.lvlibp) is output to `Builds/VI-Snippet.lvlibp`

*Note: This library was built and tested with LabVIEW 2022.*

## Contribution
Feedback is welcome, submit a ticket for bug fixes or feature requests.

Cheers,
Ryan
