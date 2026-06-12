---
title: "do-release-upgrade 12.04 LTS to 14.04 LTS fails with typeError"
date: 2015-06-15
forum: Installation &amp; Upgrades
---

### Post by dorf06 on 2015-06-15
Hello,

    I am trying to upgrade our server which is running 12.04 LTS to 14.04 LTS with do-release-upgrade. When I run the command however, I receive this error:

Reading cache




A fatal error occurred 


Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 


Traceback (most recent call last): 


File "/tmp/update-manager-ck6qDN/trusty", line 10, in <module> 
sys.exit(main()) 


File "/tmp/update-manager-ck6qDN/DistUpgrade/DistUpgradeMain.py", 
line 241, in main 
save_system_state(logdir) 


File "/tmp/update-manager-ck6qDN/DistUpgrade/DistUpgradeMain.py", 
line 134, in save_system_state 
scrub_sources=True) 


TypeError: save_state() got an unexpected keyword argument 
'scrub_sources' 
=== Command detached from window (Mon Jun 15 11:03:43 2015) ===
=== Command terminated with exit status 1 (Mon Jun 15 11:03:43 2015) ===

Here is the output of my main.log file:

2015-06-15 10:20:29,078 INFO Using config files '['./DistUpgrade.cfg.precise']'
2015-06-15 10:20:29,078 INFO uname information: 'Linux undhpcvideo 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64'
2015-06-15 10:20:29,078 INFO apt version: '0.8.16~exp12ubuntu10'
2015-06-15 10:20:29,078 INFO python version: '2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3]'
2015-06-15 10:20:29,078 INFO release-upgrader version '0.220.3' started
2015-06-15 10:20:29,079 INFO locale: 'en_US' 'UTF-8'
2015-06-15 10:20:29,175 DEBUG Using 'DistUpgradeViewText' view
2015-06-15 10:20:29,207 DEBUG aufsOptionsAndEnvironmentSetup()
2015-06-15 10:20:29,207 DEBUG using '/tmp/upgrade-rw-xOcQD5' as aufs_rw_dir
2015-06-15 10:20:29,207 DEBUG using '/tmp/upgrade-chroot-kX7J7u' as aufs chroot dir
2015-06-15 10:20:29,208 DEBUG enable dpkg --force-overwrite
2015-06-15 10:20:29,214 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2015-06-15 10:20:29,215 ERROR not handled exception:
Traceback (most recent call last):


  File "/tmp/update-manager-x6lktm/trusty", line 10, in <module>
    sys.exit(main())


  File "/tmp/update-manager-x6lktm/DistUpgrade/DistUpgradeMain.py", line 241, in main
    save_system_state(logdir)


  File "/tmp/update-manager-x6lktm/DistUpgrade/DistUpgradeMain.py", line 134, in save_system_state
    scrub_sources=True)


TypeError: save_state() got an unexpected keyword argument 'scrub_sources'

---

### Post by kellan2 on 2015-08-12
Did you ever find a solution?  I'm running into this identical bug.

---

