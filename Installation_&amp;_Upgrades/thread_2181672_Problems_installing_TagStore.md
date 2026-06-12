---
title: "Problems installing TagStore"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by WttcGTw on 2013-10-18
On my search for a GUI to search files using tags I found TagStore [http://www.tagstore.org](http://www.tagstore.org)  . I tried to install TagStore on Ubuntu 12.04 both as subversion as well as as tarball according to the installation instructions on the website.

I got stuck here (I have checked dependencies):

```
user@user:~/research_platform/tagstore$ python ./tagstore.py
[...] 
ImportError: cannot import name TsConstants 
user@user:~/research_platform/tagstore$
```

I tried to install the program in different directoires and with different settings for the environment variables PATH und PYTHONPATH without luck.

Any ideas?

---

### Post by WttcGTw on 2013-11-29
I found the answer to my own question:

After checking for dependencies and installing Tagstore according to the instructions on the[ website]("http://tagstore.org") I got the following output:

```
user@user:~$ cd tagstore-v1.2
user@user:~/tagstore-v1.2$ python tagstore_manager.py
Traceback (most recent call last):
  File "tagstore_manager.py", line 20, in <module>
    from tagstore_retag import ReTagController
  File "/home/user/tagstore-v1.2/tagstore_retag.py", line 22, in <module>
    from tscore.configwrapper import ConfigWrapper
  File "/home/user/tagstore-v1.2/tscore/configwrapper.py", line 22, in <module>
    from tscore.tsconstants import TsConstants
  File "/home/user/tagstore-v1.2/tscore/tsconstants.py", line 18, in <module>
    from tsos.filesystem import FileSystemWrapper
  File "/home/user/tagstore-v1.2/tsos/filesystem.py", line 27, in <module>
    from linux import FileSystem
  File "/home/user/tagstore-v1.2/tsos/linux.py", line 19, in <module>
    from tscore.tsconstants import TsConstants
ImportError: cannot import name TsConstants
user@user:~/tagstore-v1.2$ gedit ~/tagstore-1.2/tsos/linux.py
user@user:~/tagstore-v1.2$ gedit ~/tagstore-v1.2/tsos/linux.py
user@user:~/tagstore-v1.2$ python tagstore_manager.py
2013-11-16 19:25:58,868 - INFO - loghelper.py - 63 - APPlogger does not exist - created a new one
2013-11-16 19:25:58,874 - INFO - tagstore_manager.py - 86 - initialize configuration
2013-11-16 19:25:58,912 - INFO - admindialog.py - 1444 - TagStoreLogger
2013-11-16 19:26:00,248 - INFO - loghelper.py - 105 - STORElogger for Documents does not exist - created a new one
2013-11-16 19:26:00,314 - INFO - store.py - 282 - parent_path: 'Documents'
user@user:~/tagstore-v1.2$ 
```

Looking at the Traceback TsConstants could not be imported from file "/home/user/tagstore-v1.2/tsos/linux.py" but could be imported later on from file "/home/user/tagstore-v1.2/tscore/configwrapper.py" presumably because TsConstants have not been created when trying import in linux.py. Looking at the [diff file Changeset 187 for research_platform/tagstore/tsos/linux.py]("http://intra.ist.tugraz.at/trac/tagstore/changeset/187/research_platform/tagstore/tsos/linux.py") a line number 19 has been introduced containing 

```
from tscore.tsconstants import TsConstants

```
after commenting out this line TagStore started to work without problems.


The  TagStore Manager can be started from an application launcher or from a  script in a file manager allowing scripting with a [shell script]("http://ubuntuforums.org/showthread.php?t=1683502") like

```
sh -c "cd /your/path/to/tagstore-v1.2 && python tagstore_manager.py"
```

If your path to tagstore-v1.2 would be for example /home/Michael/ the line would be

```
sh -c "cd /home/Michael/tagstore-v1.2 && python tagstore_manager.py"
```

tagstore.py can be started automatically by changing the line

```
Exec=python /home/beyer/tagstore-v1.2/tagstore.py &
```

in file ~/.config/autostart/python.desktop to 

```
Exec=sh -c "cd /your/path/to/tagstore-v1.2 && python tagstore.py &"
```

I hope this is helpful.

---

