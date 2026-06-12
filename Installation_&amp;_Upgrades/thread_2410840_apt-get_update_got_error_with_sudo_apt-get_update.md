---
title: "apt-get update got error with sudo apt-get update"
date: 2019-01-21
forum: Installation &amp; Upgrades
---

### Post by iamquang95 on 2019-01-21
[COLOR=#1D2129][FONT=&amp]I'm using Ubuntu
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]```


```[/FONT][/COLOR]```

[COLOR=#1D2129][FONT=&amp]lsb_release -a
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]No LSB modules are available.
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Distributor ID: &nbsp; &nbsp;Ubuntu
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Description: &nbsp; &nbsp;Ubuntu 18.04.1 LTS
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Release: &nbsp; &nbsp;18.04
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Codename: &nbsp; &nbsp;bionic
[/FONT][/COLOR]

```[COLOR=#1D2129][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]

[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]The problem i got is when trying to `sudo apt-get update`
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]```
[/FONT][/COLOR][COLOR=#1D2129][FONT=&quot]Hit:1 https://deb.nodesource.com/node_10.x bionic InRelease[/FONT][/COLOR][COLOR=#1D2129][FONT=&quot]Hit:2 https://download.docker.com/linux/ubuntu bionic InRelease                                                                                                                                                   
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                                      
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:4 http://dl.google.com/linux/chrome/deb stable Release                                                                                                                                                        
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                                                                                                                                     
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:8 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease                                                                                                                                           
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:5 https://packages.cloud.google.com/apt kubernetes-xenial InRelease                                                                                                                                           
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:9 http://vn.archive.ubuntu.com/ubuntu bionic InRelease                                                                                
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:10 https://dl.yarnpkg.com/debian stable InRelease                                                                                     
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Hit:11 http://vn.archive.ubuntu.com/ubuntu bionic-updates InRelease     
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Get:12 http://vn.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Fetched 158 kB in 4s (43.2 kB/s)     
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Error: Timeout was reached
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Traceback (most recent call last):
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/cnf-update-db", line 8, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    from CommandNotFound.db.creator import DbCreator
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    import apt_pkg
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Error in sys.excepthook:
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Traceback (most recent call last):
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    from apport.fileutils import likely_packaged, get_recent_crashes
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    from apport.report import Report
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    import apport.fileutils
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    from apport.packaging_impl import impl as packaging
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    import apt
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    import apt_pkg
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]

[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Original exception was:
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Traceback (most recent call last):
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/cnf-update-db", line 8, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    from CommandNotFound.db.creator import DbCreator
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]    import apt_pkg
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]Reading package lists... Done
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot]E: Sub-process returned an error code


[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&quot][/FONT][/COLOR]

```[COLOR=#1D2129][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]The reason i had this error is that i tried to run `sudo apt-get upgrade`. [/FONT][/COLOR][COLOR=#1D2129][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]It's seem related to <a href="https://ubuntuforums.org/showthread.php?t=2398895" target="_blank">https://ubuntuforums.org/showthread.php?t=2398895</a> . But i tried all solution that mentioned in this thread but i still have this error.
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Moreover, i tried to 
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]```


```[/FONT][/COLOR]```
[COLOR=#1D2129][FONT=&amp]wget https://launchpad.net/ubuntu/+archive/primary/+files/libapt-pkg5.0_1.2.29_amd64.deb
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]sudo dpkg --install --force-downgrade libapt-pkg5.0.1.2.29
[/FONT][/COLOR]

```[COLOR=#1D2129][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]As mentioned in <a href="https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1644643" target="_blank">https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1644643</a>.
[/FONT][/COLOR][COLOR=#1D2129][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Can anyone help me with this error <img src="images/smilies/icon_sad.gif" border="0" alt="" title="Sad" smilieid="11" class="inlineimg"> 
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=&amp]Thanks.


[/FONT][/COLOR]

---

