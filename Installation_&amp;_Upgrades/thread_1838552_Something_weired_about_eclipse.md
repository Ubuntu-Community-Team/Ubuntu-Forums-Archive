---
title: "Something weired about eclipse"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by KanHuang on 2011-09-03
I installed the pyqt4 packages, pydev and eclipse.
The qt scripts run well when I use 'python somescript' in terminal, but the eclipse just can't find the libs for qt no matter how I set the interpretor or external libraries. 

What's interesting is finally I want to try install qt eclipse integration and I extract it in the wrong directory, which should be /usr/lib/(I put it into /usr/lib/eclipse). Then my eclipse can't work. When I want to start it from terminal. It shows 'I don't have permission to the file /usr/lib/eclipse/eclipse.

I can't solve this problem. So I try to reinstall eclipse. It works. And by the way, it now can find the qt libs and I don't have to switch to other IDEs. It's so weired. And I just reinstall eclipse. Could anyone explain this?

By the way, the eclipse still can not find the gtk package. When I download some project like exaile from launchpad and run the code in eclipse, it shows 

Finding files... done.
Importing test modules ... Usage: runfiles.py [options]

runfiles.py: error: no such option: --port
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/dist_plugin.py", line 45, in <module>
    options, args = p.parse_args()
  File "/usr/lib/python2.6/optparse.py", line 1396, in parse_args
    self.error(str(err))
  File "/usr/lib/python2.6/optparse.py", line 1578, in error
    self.exit(2, "%s: error: %s\n" % (self.get_prog_name(), msg))
  File "/usr/lib/python2.6/optparse.py", line 1568, in exit
    sys.exit(status)
SystemExit: 2
ERROR: Module: plugins.dist_plugin could not be imported (file: /home/huangkan/workspace/exaile/plugins/dist_plugin.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/multialarmclock/__init__.py", line 21, in <module>
    import gtk, time, glib, thread, os
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.multialarmclock.cellrenderers could not be imported (file: /home/huangkan/workspace/exaile/plugins/multialarmclock/cellrenderers.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/multialarmclock/__init__.py", line 21, in <module>
    import gtk, time, glib, thread, os
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.multialarmclock.macprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/multialarmclock/macprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/streamripper/__init__.py", line 18, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.streamripper.srprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/streamripper/srprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/contextinfo/__init__.py", line 4, in <module>
    from xlgui import panel, guiutil, playlist, menu
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.contextinfo.pylast could not be imported (file: /home/huangkan/workspace/exaile/plugins/contextinfo/pylast.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/contextinfo/__init__.py", line 4, in <module>
    from xlgui import panel, guiutil, playlist, menu
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.contextinfo.inspector could not be imported (file: /home/huangkan/workspace/exaile/plugins/contextinfo/inspector.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/contextinfo/__init__.py", line 4, in <module>
    from xlgui import panel, guiutil, playlist, menu
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.contextinfo.contextprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/contextinfo/contextprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.daapserverprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/daapserverprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.server could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/server.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.config could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/config.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.zeroconf could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/zeroconf.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.cache could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/cache.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.playlists could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/playlists.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.daap could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/daap.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.metadata could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/metadata.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.containers could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/containers.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.server could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/server.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.daap_data could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/daap_data.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.avi could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/avi.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.exaile could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/exaile.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.mp3 could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/mp3.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.vorbis could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/vorbis.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.ogg could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/ogg.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.mov could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/mov.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapserver/__init__.py", line 5, in <module>
    import spydaap.parser.exaile
  File "/home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/__init__.py", line 17, in <module>
    from spydaap.daap import do
ImportError: No module named spydaap.daap
ERROR: Module: plugins.daapserver.spydaap.parser.flac could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapserver/spydaap/parser/flac.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/bookmarks/__init__.py", line 21, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.bookmarks.bookmarksprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/bookmarks/bookmarksprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/librivox/__init__.py", line 22, in <module>
    import gtk, gobject, os
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.librivox.librivoxsearch could not be imported (file: /home/huangkan/workspace/exaile/plugins/librivox/librivoxsearch.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/librivox/__init__.py", line 22, in <module>
    import gtk, gobject, os
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.librivox.about_window could not be imported (file: /home/huangkan/workspace/exaile/plugins/librivox/about_window.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/audioscrobbler/__init__.py", line 18, in <module>
    import asprefs
  File "/home/huangkan/workspace/exaile/plugins/audioscrobbler/asprefs.py", line 18, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.audioscrobbler.asprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/audioscrobbler/asprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/audioscrobbler/__init__.py", line 18, in <module>
    import asprefs
  File "/home/huangkan/workspace/exaile/plugins/audioscrobbler/asprefs.py", line 18, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.audioscrobbler._scrobbler could not be imported (file: /home/huangkan/workspace/exaile/plugins/audioscrobbler/_scrobbler.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/replaygain/replaygainprefs.py", line 28, in <module>
    from xlgui.preferences import widgets
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.replaygain.replaygainprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/replaygain/replaygainprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapclient/__init__.py", line 19, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.daapclient.daap could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapclient/daap.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/daapclient/__init__.py", line 19, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.daapclient.daap_data could not be imported (file: /home/huangkan/workspace/exaile/plugins/daapclient/daap_data.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/screensaverpause/__init__.py", line 28, in <module>
    import dbus, gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.screensaverpause.prefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/screensaverpause/prefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/cd/__init__.py", line 49, in <module>
    import cdprefs
  File "/home/huangkan/workspace/exaile/plugins/cd/cdprefs.py", line 29, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.cd.cdprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/cd/cdprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/cd/__init__.py", line 49, in <module>
    import cdprefs
  File "/home/huangkan/workspace/exaile/plugins/cd/cdprefs.py", line 29, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.cd._cdguipanel could not be imported (file: /home/huangkan/workspace/exaile/plugins/cd/_cdguipanel.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/cd/__init__.py", line 49, in <module>
    import cdprefs
  File "/home/huangkan/workspace/exaile/plugins/cd/cdprefs.py", line 29, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.cd.importer could not be imported (file: /home/huangkan/workspace/exaile/plugins/cd/importer.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/podcasts/__init__.py", line 1, in <module>
    import gtk, glib
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.podcasts._feedparser could not be imported (file: /home/huangkan/workspace/exaile/plugins/podcasts/_feedparser.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/amazoncovers/__init__.py", line 18, in <module>
    import amazonprefs
  File "/home/huangkan/workspace/exaile/plugins/amazoncovers/amazonprefs.py", line 18, in <module>
    from xlgui.preferences import widgets
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.amazoncovers._ecs could not be imported (file: /home/huangkan/workspace/exaile/plugins/amazoncovers/_ecs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/amazoncovers/__init__.py", line 18, in <module>
    import amazonprefs
  File "/home/huangkan/workspace/exaile/plugins/amazoncovers/amazonprefs.py", line 18, in <module>
    from xlgui.preferences import widgets
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.amazoncovers.amazonprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/amazoncovers/amazonprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.menu could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/menu.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.jamapi could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/jamapi.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.jamtree could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/jamtree.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.decoder could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/decoder.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tool could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tool.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.scanner could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/scanner.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.encoder could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/encoder.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_encode_basestring_ascii could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_encode_basestring_ascii.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_check_circular could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_check_circular.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_indent could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_indent.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_unicode could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_unicode.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_pass3 could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_pass3.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_pass2 could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_pass2.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_float could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_float.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_default could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_default.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_separators could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_separators.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_dump could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_dump.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_scanstring could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_scanstring.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_recursion could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_recursion.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_fail could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_fail.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_pass1 could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_pass1.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/jamendo/__init__.py", line 28, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.jamendo.simplejson.tests.test_decode could not be imported (file: /home/huangkan/workspace/exaile/plugins/jamendo/simplejson/tests/test_decode.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/moodbar/__init__.py", line 18, in <module>
    import moodbarprefs
  File "/home/huangkan/workspace/exaile/plugins/moodbar/moodbarprefs.py", line 19, in <module>
    from xlgui.preferences import widgets
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.moodbar.moodbarprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/moodbar/moodbarprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/awn/__init__.py", line 22, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.awn.awn_prefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/awn/awn_prefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/desktopcover/__init__.py", line 20, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.desktopcover.desktopcover_preferences could not be imported (file: /home/huangkan/workspace/exaile/plugins/desktopcover/desktopcover_preferences.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/ipconsole/__init__.py", line 21, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.ipconsole.ipconsoleprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/ipconsole/ipconsoleprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/ipconsole/__init__.py", line 21, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.ipconsole.ipython_view could not be imported (file: /home/huangkan/workspace/exaile/plugins/ipconsole/ipython_view.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/lastfmlove/__init__.py", line 16, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.lastfmlove.pylast could not be imported (file: /home/huangkan/workspace/exaile/plugins/lastfmlove/pylast.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/lastfmlove/__init__.py", line 16, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.lastfmlove.cellrenderertoggleimage could not be imported (file: /home/huangkan/workspace/exaile/plugins/lastfmlove/cellrenderertoggleimage.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/lastfmlove/__init__.py", line 16, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.lastfmlove.lastfmlove_preferences could not be imported (file: /home/huangkan/workspace/exaile/plugins/lastfmlove/lastfmlove_preferences.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/notify/__init__.py", line 20, in <module>
    import pynotify
  File "/usr/lib/pymodules/python2.6/gtk-2.0/pynotify/__init__.py", line 1, in <module>
    from _pynotify import *
ImportError: could not import gtk
ERROR: Module: plugins.notify.notifyprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/notify/notifyprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/alarmclock/__init__.py", line 1, in <module>
    import gtk, time, glib, thread
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.alarmclock.acprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/alarmclock/acprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/minimode/__init__.py", line 18, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.minimode.minimode_preferences could not be imported (file: /home/huangkan/workspace/exaile/plugins/minimode/minimode_preferences.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/minimode/__init__.py", line 18, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.minimode.controls could not be imported (file: /home/huangkan/workspace/exaile/plugins/minimode/controls.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/plugins/notifyosd/__init__.py", line 34, in <module>
    from xlgui import icons
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: plugins.notifyosd.notifyosdprefs could not be imported (file: /home/huangkan/workspace/exaile/plugins/notifyosd/notifyosdprefs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
ImportError: No module named data.migrations.migration_200907100931.oldtrack
ERROR: Module: data.migrations.migration_200907100931.oldtrack could not be imported (file: /home/huangkan/workspace/exaile/data/migrations/migration_200907100931/oldtrack.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
ImportError: No module named data.migrations.migration_200907100931.oldexailelib
ERROR: Module: data.migrations.migration_200907100931.oldexailelib could not be imported (file: /home/huangkan/workspace/exaile/data/migrations/migration_200907100931/oldexailelib.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
ImportError: No module named data.migrations.migration_200907100931.xlmisc
ERROR: Module: data.migrations.migration_200907100931.xlmisc could not be imported (file: /home/huangkan/workspace/exaile/data/migrations/migration_200907100931/xlmisc.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
ImportError: No module named data.migrations.migration_200907100931.olddb
ERROR: Module: data.migrations.migration_200907100931.olddb could not be imported (file: /home/huangkan/workspace/exaile/data/migrations/migration_200907100931/olddb.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.playlist could not be imported (file: /home/huangkan/workspace/exaile/xlgui/playlist.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.properties could not be imported (file: /home/huangkan/workspace/exaile/xlgui/properties.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.progress could not be imported (file: /home/huangkan/workspace/exaile/xlgui/progress.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.accelerators could not be imported (file: /home/huangkan/workspace/exaile/xlgui/accelerators.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.menu could not be imported (file: /home/huangkan/workspace/exaile/xlgui/menu.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.tray could not be imported (file: /home/huangkan/workspace/exaile/xlgui/tray.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.devices could not be imported (file: /home/huangkan/workspace/exaile/xlgui/devices.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.collection could not be imported (file: /home/huangkan/workspace/exaile/xlgui/collection.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.guiutil could not be imported (file: /home/huangkan/workspace/exaile/xlgui/guiutil.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.icons could not be imported (file: /home/huangkan/workspace/exaile/xlgui/icons.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.oldmenu could not be imported (file: /home/huangkan/workspace/exaile/xlgui/oldmenu.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.osd could not be imported (file: /home/huangkan/workspace/exaile/xlgui/osd.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.cover could not be imported (file: /home/huangkan/workspace/exaile/xlgui/cover.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.main could not be imported (file: /home/huangkan/workspace/exaile/xlgui/main.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.playlist_columns could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/playlist_columns.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.dialogs could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/dialogs.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.rating could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/rating.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.info could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/info.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.queue could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/queue.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.playlist could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/playlist.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.menu could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/menu.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.playback could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/playback.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.common could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/common.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.notebook could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/notebook.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.filter could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/filter.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.widgets.menuitems could not be imported (file: /home/huangkan/workspace/exaile/xlgui/widgets/menuitems.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.files could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/files.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.playlists could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/playlists.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.radio could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/radio.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.device could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/device.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.collection could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/collection.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.panel.flatplaylist could not be imported (file: /home/huangkan/workspace/exaile/xlgui/panel/flatplaylist.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.widgets could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/widgets.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.playlists could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/playlists.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.playback could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/playback.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.appearance could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/appearance.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.collection could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/collection.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.plugin could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/plugin.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.osd could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/osd.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/xlgui/__init__.py", line 30, in <module>
    import gtk
  File "/home/huangkan/Downloads/pygtk-2.24.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
ERROR: Module: xlgui.preferences.cover could not be imported (file: /home/huangkan/workspace/exaile/xlgui/preferences/cover.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/tests/xl/trax/test_search.py", line 1, in <module>
    import mox
ImportError: No module named mox
ERROR: Module: tests.xl.trax.test_search could not be imported (file: /home/huangkan/workspace/exaile/tests/xl/trax/test_search.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/tests/xl/trax/test_util.py", line 3, in <module>
    import mox
ImportError: No module named mox
ERROR: Module: tests.xl.trax.test_util could not be imported (file: /home/huangkan/workspace/exaile/tests/xl/trax/test_util.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
  File "/home/huangkan/workspace/exaile/tests/xl/trax/test_track.py", line 12, in <module>
    import mox
ImportError: No module named mox
ERROR: Module: tests.xl.trax.test_track could not be imported (file: /home/huangkan/workspace/exaile/tests/xl/trax/test_track.py).
Traceback (most recent call last):
  File "/home/huangkan/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.python.pydev.debug_2.0.0.2011040403/pysrc/pydev_runfiles.py", line 307, in __get_module_from_str
    mod = __import__(modname)
ImportError: No module named doc.conf
ERROR: Module: doc.conf could not be imported (file: /home/huangkan/workspace/exaile/doc/conf.py).
done.

----------------------------------------------------------------------
Ran 0 tests in 0.000s

OK


What should I do?

---

