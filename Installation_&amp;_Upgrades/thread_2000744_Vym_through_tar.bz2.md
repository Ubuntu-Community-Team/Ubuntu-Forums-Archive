---
title: "Vym through tar.bz2"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by xxsmarty on 2012-06-10
How to install vym through a tar.bz2 file .
I have always got problems with such files.
Please Help me.
This file I got from a CD.

---

### Post by MG&amp;TL on 2012-06-10
Extract the file:

```
bunzip2 file.tar.bz2
tar xvf file.tar
```

Then show us what's inside it:

```
ls file
```

So we can find out how to help.

On a side note, you can get vym in the software centre, why are you using a tarball?

---

### Post by xxsmarty on 2012-06-10
Ya i have now.
but can you tell me how to install such files for future reference. here is ls
```

aboutdialog.cpp         flagobj.cpp                 ornamentedobj.cpp
aboutdialog.h           flagobj.h                   ornamentedobj.h
adaptormodel.cpp        flagrow.cpp                 parser.cpp
adaptormodel.h          flagrow.h                   parser.h
animpoint.cpp           flagrowobj.cpp              process.cpp
animpoint.h             flagrowobj.h                process.h
attribute.cpp           flags                       README.txt
attributedelegate.cpp   floatimageobj.cpp           scripts
attributedelegate.h     floatimageobj.h             settings.cpp
attributedialog.cpp     floatobj.cpp                settings.h
attributedialog.h       floatobj.h                  shortcuts.cpp
attributedialog.ui      frameobj.cpp                shortcuts.h
attribute.h             frameobj.h                  showtextdialog.cpp
attributeitem.cpp       geometry.cpp                showtextdialog.h
attributeitem.h         geometry.h                  showtextdialog.ui
attributewidget.cpp     headingeditor.cpp           simplescripteditor.cpp
attributewidget.h       headingeditor.h             simplescripteditor.h
attributewidget.ui      headingobj.cpp              simplescripteditor.ui
branchitem.cpp          headingobj.h                styles
branchitem.h            highlighter.cpp             tex
branchobj.cpp           highlighter.h               texteditor.cpp
branchobj.h             historywindow.cpp           texteditor.h
branchpropwindow.cpp    historywindow.h             treedelegate.cpp
branchpropwindow.h      historywindow.ui            treedelegate.h
branchpropwindow.ui     icons                       treeeditor.cpp
bugagent.cpp            imageitem.cpp               treeeditor.h
bugagent.h              imageitem.h                 treeitem.cpp
demos                   imageobj.cpp                treeitem.h
doc                     imageobj.h                  treemodel.cpp
downloadagent.cpp       imports.cpp                 treemodel.h
downloadagent.h         imports.h                   version.cpp
editxlinkdialog.cpp     INSTALL.txt                 version.h
editxlinkdialog.h       lang                        vym.changelog
editxlinkdialog.ui      LICENSE.txt                 vymmodel.cpp
exporthtmldialog.cpp    linkablemapobj.cpp          vymmodel.h
exporthtmldialog.h      linkablemapobj.h            vym.pro
exporthtmldialog.ui     macros                      vym.rc
exportoofiledialog.cpp  main.cpp                    vymview.cpp
exportoofiledialog.h    mainwindow.cpp              vymview.h
exports                 mainwindow.h                warningdialog.cpp
exports.cpp             mapeditor.cpp               warningdialog.h
exports.h               mapeditor.h                 warningdialog.ui
exportxhtmldialog.ui    mapitem.cpp                 xlink.cpp
extrainfodialog.cpp     mapitem.h                   xlink.h
extrainfodialog.h       mapobj.cpp                  xlinkitem.cpp
extrainfodialog.ui      mapobj.h                    xlinkitem.h
file.cpp                misc.cpp                    xlinkobj.cpp
file.h                  misc.h                      xlinkobj.h
findresultitem.cpp      mkdtemp.cpp                 xml-base.cpp
findresultitem.h        mkdtemp.h                   xml-base.h
findresultmodel.cpp     mysortfilterproxymodel.cpp  xml-freemind.cpp
findresultmodel.h       mysortfilterproxymodel.h    xml-freemind.h
findresultwidget.cpp    noteeditor.cpp              xmlobj.cpp
findresultwidget.h      noteeditor.h                xmlobj.h
findwidget.cpp          noteobj.cpp                 xml-vym.cpp
findwidget.h            noteobj.h                   xml-vym.h
flag.cpp                options.cpp                 xsltproc.cpp
flag.h                  options.h                   xsltproc.h





```

---

### Post by MG&amp;TL on 2012-06-10
I'm afraid there isn't a "standard way" to install these files. They're typically source code files that need to be compiled, and if you're lucky (and you are) the developer has included a README file to tell you what to do. Post the contents of the README file.

(although I have to say, this is looking like a non-standard install.)

---

### Post by xxsmarty on 2012-06-10
Here is the content:
```

VYM - View Your Mind - 2.0.0  (c) 2007-2011 by Uwe Drechsel
===========================================================

Binaries
--------

To get binaries for this version, please check

    http://download.opensuse.org/repositories/home%3A//insilmaril/


Documentation
-------------

The complete documentation of vym is available as PDF document in
english and spanish. It can be accessed directly from vym if a PDF
viewer is installed. It also can be downloaded from the vym site at
Sourceforge:

    https://sourceforge.net/projects/vym/


Questions and feedback
----------------------

Please direct questions to the mailinglist first: 

    vym-forum@lists.sourceforge.net






```

---

### Post by Toz on 2012-06-10
Vym is also in the ubuntu repositories. You could just install it from the Software Centre without having to compile anything.

---

