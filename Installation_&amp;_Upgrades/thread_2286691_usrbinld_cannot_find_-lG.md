---
title: "/usr/bin/ld: cannot find -lG"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by GMask on 2015-07-14
Hello 

I am trying to install edb (evan's debugger) but I get the following compilation error after "make" command:


```

parallels@ubuntu:~/edb-debugger$ make
cd src/ && ( test -e Makefile || /usr/lib/x86_64-linux-gnu/qt5/bin/qmake /home/parallels/edb-debugger/src/src.pro -o Makefile ) && make -f Makefile 
make[1]: Entering directory `/home/parallels/edb-debugger/src'
g++ -m64 -rdynamic -Wl,-O1 -o ../edb .release-shared/obj/ArchProcessor.o .release-shared/obj/BasicBlock.o .release-shared/obj/BinaryString.o .release-shared/obj/ByteShiftArray.o .release-shared/obj/CommentServer.o .release-shared/obj/Configuration.o .release-shared/obj/DataViewInfo.o .release-shared/obj/Debugger.o .release-shared/obj/DialogArguments.o .release-shared/obj/DialogAttach.o .release-shared/obj/DialogInputBinaryString.o .release-shared/obj/DialogInputValue.o .release-shared/obj/DialogMemoryRegions.o .release-shared/obj/DialogOptions.o .release-shared/obj/DialogPlugins.o .release-shared/obj/DialogThreads.o .release-shared/obj/FixedFontSelector.o .release-shared/obj/Function.o .release-shared/obj/HexStringValidator.o .release-shared/obj/Instruction.o .release-shared/obj/LineEdit.o .release-shared/obj/MD5.o .release-shared/obj/MemoryRegions.o .release-shared/obj/PluginModel.o .release-shared/obj/ProcessModel.o .release-shared/obj/QDisassemblyView.o .release-shared/obj/QLongValidator.o .release-shared/obj/QULongValidator.o .release-shared/obj/RecentFileManager.o .release-shared/obj/RegionBuffer.o .release-shared/obj/Register.o .release-shared/obj/RegisterListWidget.o .release-shared/obj/RegisterViewDelegate.o .release-shared/obj/State.o .release-shared/obj/SymbolManager.o .release-shared/obj/SyntaxHighlighter.o .release-shared/obj/TabWidget.o .release-shared/obj/ThreadsModel.o .release-shared/obj/edb.o .release-shared/obj/main.o .release-shared/obj/qhexview.o .release-shared/obj/qrc_debugger.o .release-shared/obj/moc_ArchProcessor.o .release-shared/obj/moc_BinaryString.o .release-shared/obj/moc_CommentServer.o .release-shared/obj/moc_Debugger.o .release-shared/obj/moc_DialogArguments.o .release-shared/obj/moc_DialogAttach.o .release-shared/obj/moc_DialogInputBinaryString.o .release-shared/obj/moc_DialogInputValue.o .release-shared/obj/moc_DialogMemoryRegions.o .release-shared/obj/moc_DialogOptions.o .release-shared/obj/moc_DialogPlugins.o .release-shared/obj/moc_DialogThreads.o .release-shared/obj/moc_FixedFontSelector.o .release-shared/obj/moc_LineEdit.o .release-shared/obj/moc_MemoryRegions.o .release-shared/obj/moc_PluginModel.o .release-shared/obj/moc_ProcessModel.o .release-shared/obj/moc_QDisassemblyView.o .release-shared/obj/moc_RecentFileManager.o .release-shared/obj/moc_RegionBuffer.o .release-shared/obj/moc_RegisterListWidget.o .release-shared/obj/moc_SyntaxHighlighter.o .release-shared/obj/moc_TabWidget.o .release-shared/obj/moc_ThreadsModel.o .release-shared/obj/moc_qhexview.o   -L/usr/X11R6/lib64 -lQt5XmlPatterns -L/usr/lib/x86_64-linux-gnu -lQt5Widgets -lQt5Network -lQt5Xml -lQt5Gui -lQt5Core -lGL -lpthread 
/usr/bin/ld: cannot find -lGL
collect2: error: ld returned 1 exit status
make[1]: *** [../edb] Error 1
make[1]: Leaving directory `/home/parallels/edb-debugger/src'
make: *** [sub-src-make_first] Error 2



```



Would you please tell me what should I do?

Thanks

---

### Post by steeldriver on 2015-07-14
Hello and welcome to the forums

Your system doesn't seem to have the libGL development library: the default one is provided as part of the Mesa OpenGL implementation, I think 

```

sudo apt-get install libgl1-mesa-dev

```

or install it from the Software Center

---

### Post by GMask on 2015-07-14
I already did this but does not work give me the same error!

---

### Post by GMask on 2015-07-14
It is solved I forgot to restart the ubuntu after installation and that was the reason!

Thank you for your help :)

---

