---
title: "Installed Qt4 but errors when type 'make'"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by maxguan on 2008-03-14
Hello everyone
          The story is that my computer is ubuntu7.10. I updated and installed Qt4. It is okay to run qmake && make. Everything is fine.

However. I am trying to install the same software on other computer which is Ubuntu 5.10. The software required >=Qt4.2. So, I installed Qt4.2.3 through package manager. It is fine when I type 'qmake' but 'make' has problems...

```
src/ApplicationWindow.cpp:13844: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp:13848: error: ‘class MdiSubWindow’ has no member named ‘inherits’
src/ApplicationWindow.cpp:13852: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp:13856: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp:13860: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp:13865: error: ‘class MdiSubWindow’ has no member named ‘objectName’
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::dropFolderItems(Q3ListViewItem*)’:
src/ApplicationWindow.cpp:14018: error: ‘class MdiSubWindow’ has no member named ‘hide’
src/ApplicationWindow.cpp: In member function ‘QString ApplicationWindow::generateUniqueName(const src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::cascade()’:
src/ApplicationWindow.cpp:14318: error: ‘QMdiSubWindow’ was not declared in this scope
src/ApplicationWindow.cpp:14318: error: template argument 1 is invalid
src/ApplicationWindow.cpp:14318: error: invalid type in declaration before ‘=’ token
src/ApplicationWindow.cpp:14318: error: invalid use of undefined type ‘struct QMdiArea’
src/ApplicationWindow.h:65: error: forward declaration of ‘struct QMdiArea’
src/ApplicationWindow.cpp:14318: error: incomplete type ‘QMdiArea’ used in nested name specifier
/usr/include/qt4/QtCore/qglobal.h: At global scope:
/usr/include/qt4/QtCore/qglobal.h: In instantiation of ‘QForeachContainer<int>’:
src/ApplicationWindow.cpp:14319:   instantiated from here
/usr/include/qt4/QtCore/qglobal.h:1693: error: ‘int’ is not a class, struct, or union type
/usr/include/qt4/QtCore/qglobal.h:1693: error: ‘int’ is not a class, struct, or union type
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::cascade()’:
src/ApplicationWindow.cpp:14319: error: ‘class QForeachContainer<int>’ has no member named ‘i’
src/ApplicationWindow.cpp:14319: error: ‘class QForeachContainer<int>’ has no member named ‘e’
src/ApplicationWindow.cpp:14319: error: ‘class QForeachContainer<int>’ has no member named ‘i’
src/ApplicationWindow.cpp:14319: error: ‘w’ was not declared in this scope
src/ApplicationWindow.cpp:14319: error: ‘class QForeachContainer<int>’ has no member named ‘i’
src/ApplicationWindow.cpp: At global scope:
src/ApplicationWindow.cpp:14330: warning: unused parameter ‘fn’
src/ApplicationWindow.cpp:14330: warning: unused parameter ‘execute’
src/ApplicationWindow.cpp:14330: warning: unused parameter ‘factorySettings’
src/ApplicationWindow.cpp: In member function ‘MultiLayer* ApplicationWindow::generate2DGraph(Graph::CurveType)’:
src/ApplicationWindow.cpp:14371: error: ‘class MdiSubWindow’ has no member named ‘inherits’
src/ApplicationWindow.cpp:14378: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::scriptsDirPathChanged(const QString&)’:
src/ApplicationWindow.cpp:14497: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::showToolBarsMenu()’:
src/ApplicationWindow.cpp:14568: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::setMatrixUndoStackSize(int)’:
src/ApplicationWindow.cpp:15005: error: ‘class MdiSubWindow’ has no member named ‘isA’
src/ApplicationWindow.cpp:15008: error: ‘class QUndoStack’ has no member named ‘setUndoLimit’
src/ApplicationWindow.cpp: In member function ‘void ApplicationWindow::repaintWindows()’:
src/ApplicationWindow.cpp:15022: error: invalid use of undefined type ‘struct QMdiArea’
src/ApplicationWindow.h:65: error: forward declaration of ‘struct QMdiArea’
src/ApplicationWindow.cpp:15031: error: ‘class MdiSubWindow’ has no member named ‘setFocus’
src/ApplicationWindow.cpp:15033: error: ‘class MdiSubWindow’ has no member named ‘setFocus’
/usr/include/qt4/QtCore/qglobal.h: In constructor ‘QForeachContainer<T>::QForeachContainer(const T&) [with T = int]’:
src/ApplicationWindow.cpp:14319:   instantiated from here
/usr/include/qt4/QtCore/qglobal.h:1690: error: using invalid field ‘QForeachContainer<T>::i’
/usr/include/qt4/QtCore/qglobal.h:1690: error: request for member ‘begin’ in ‘((QForeachContainer<int>*)this)->QForeachContainer<int>::c’, which is of non-class type ‘const int’
/usr/include/qt4/QtCore/qglobal.h:1690: error: using invalid field ‘QForeachContainer<T>::e’
/usr/include/qt4/QtCore/qglobal.h:1690: error: request for member ‘end’ in ‘((QForeachContainer
```


Is there any other components should I install along with Qt4??
I tried to update this Ubuntu 5.10. But the repos are down. I can not connect to the network mirror (I use my school network, I can update my ubuntu7.10, but 5.10 has failed)

How should I solve this problem? Thank you

---

