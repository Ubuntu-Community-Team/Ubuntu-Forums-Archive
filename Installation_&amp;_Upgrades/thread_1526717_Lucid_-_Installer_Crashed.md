---
title: "Lucid - Installer Crashed"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2010-07-08
Hi folks,

I have been working on creating iso image that performs automatically installation 
unattended installation) on Lucid.  I used **ubiquity-frontend-kde** and **ubiquity** tools.
The installation was working properly the last time I built ( about 1 month back) .. 
I rebuilt the image with the same build procedure, and the same preseed file that worked
before ...  and of course the packages are the most recent packages from Lucid distribution .. 

And I got the error - Installer Crash with the following message:
==========================
Traceback (most recent call last)
File"/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>  main(oem_config)
File"/usr/lib/ubiquity/bin/ubiquity", line 511, in main  install (query-options.query)
File"/usr/lib/ubiquity/bin/ubiquity", line 242, in install ret=wizard.run()
File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 460, in run self.progress_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 848, in  progress_loop    
       ret=dbfilter.run_command(auto_process=True)
File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 191, in run_command 
       set.start(auto_process=auto_process)
File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 92, in start prep=self.prepare()
File "/usr/lib/ubiquity/ubiquity/components/install.py", line 41, in prepare bootdev=misc.grub_default()
File "/usr/lib/ubiquity/ubiquity/misc.py", line 97, in helper return func(*args, **kwargs)
File "/usr/lib/ubiquity/ubiquity/misc.py", line 164, in grub_default stdout=subprocess.PIPE)
File "/usr/lib/python2.6/subprocess.py", line 633, in __init__ errread, errwrite)
File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child raise_child_exdeption
OSError:[Errno 2] No Such file or directory
===============================

Is there something that I missed or any suggestion ?

Thanks,

Dang

---

### Post by uonedang on 2010-07-16
Problem resolved .. Missing the grub-common package.
 
Install the grub-common package ==> works fine.
 
Thanks
 
Dang

---

