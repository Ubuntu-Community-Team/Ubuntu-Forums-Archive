---
title: "unable to remove package ooolatex: unable to locate &lt;UNNAMED&gt; file"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Jasy jatere on 2008-02-05
Hello,
I installed the package ooolatex on xubuntu 7.10 , but it is broken and blocks any new installs. I tried to remove it with

aptitude -f install 
aptitude remove ooolatex
dpkg -r ooolatex

The system then complains that the package is in a bad state and that I should reinstall it. I tried the following

aptitude install ooolatex
aptitude reinstall ooolatex
dpkg -i ooolatex ooolatex_3.0-1_i386.deb 

But all of them complain that the package is broken. The strangest thing is that the main error message is that a file  with the name ' ' (i.e. empty string) is missing. I know that I can simply touch files to create them for removal, but what about requirements for a file which has no name? Any ideas what to do about this?
Thanks
jj

====
root@Kandy:~# aptitude -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  app-install-data-commercial 
The following NEW packages will be installed:
  epstool 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/119kB of archives. After unpacking 324kB will be used.
Do you want to continue? [Y/n/?] Y
**E: I wasn't able to locate file for the ooolatex package. This might mean you need to manually fix this package.**


=====

root@Kandy:~# aptitude remove ooolatex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  app-install-data-commercial 
The following packages will be REMOVED:
  ooolatex 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 184kB will be freed.
Writing extended state information... Done
dpkg: error processing ooolatex (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ooolatex
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing packaroot@Kandy:~# dpkg -r ooolatex
dpkg: error processing ooolatex (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ooolatex
ge states... Done
Building tag database... Done  


=====
root@Kandy:~# dpkg -r ooolatex
dpkg: error processing ooolatex (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ooolatex

=====

root@Kandy:~# aptitude install ooolatex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  epstool 
The following packages have been kept back:
  app-install-data-commercial 
The following NEW packages will be installed:
  epstool 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/119kB of archives. After unpacking 324kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
**E: I wasn't able to locate file for the ooolatex package. This might mean you need to manually fix this package.**

=====


aptitude reinstall ooolatex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ooolatex 
The following packages have been kept back:
  app-install-data-commercial 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  ooolatex: Depends: epstool but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the ooolatex package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
ooolatex

Score is 121

Accept this solution? [Y/n/q/?] Y
The following packages will be automatically REMOVED:
  ooolatex 
The following packages have been kept back:
  app-install-data-commercial 
The following packages will be REMOVED:
  ooolatex 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 184kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing ooolatex (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ooolatex
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   


=====
dpkg -i ooolatex_3.0-1_i386.deb 
(Reading database ... 159881 files and directories currently installed.)
Preparing to replace ooolatex 3.0-1 (using ooolatex_3.0-1_i386.deb) ...
Unpacking replacement ooolatex ...
id: flo: No such user
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
id: flo: No such user
dpkg: error processing ooolatex_3.0-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
id: flo: No such user
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ooolatex_3.0-1_i386.deb

---

### Post by jrib on 2008-02-05
```
dpkg --purge --force-remove-reinstreq ooolatex
```

will probably remove it.  But you will want to install it and remove it properly afterwards.

Did the package install without errors?  Paste the contents of /var/lib/dpkg/info/oolatex.*

---

### Post by Jasy jatere on 2008-02-06
Hi Jason,
thanks for your quick reply. I had actually tried the purge option, but without the force switch you suggest. This did not solve the problem. I finally decided that a reinstall over lunch would solve my problem as well, so I went for that instead of spending hours on how to find the right solution. For the moment, it seems wise to keep your hands of ooolatex, besides the packaging problem, its documentation is very unclear. 
Anyway, thanks a lot for your help
JJ

---

### Post by one_ro on 2008-07-15
Hi all,

> **_jason said:**
> ```
dpkg --purge --force-remove-reinstreq ooolatex
```will probably remove it.  But you will want to install it and remove it properly afterwards.

Did the package install without errors?  Paste the contents of /var/lib/dpkg/info/oolatex.*

I'm coming back to this post, trying to find a solution to this problem:

$ sudo dpkg --purge --force-remove-reinstreq ooolatex
(Reading database ... 202237 files and directories currently installed.)
Removing ooolatex ...
sed: can't read /usr/lib/openoffice/share/config/soffice.cfg/modules/simpress/accelerator/default.xml/default.xml: Not a directory
dpkg: error processing ooolatex (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ooolatex

Synaptic complains that ooolatex is in a very bad shape so it can't remove it either. And neither a packeg reinstall works... does anyone have a solution?

Thanks in advance,
Adrian

---

### Post by one_ro on 2008-07-15
Oh, I just found the solution...

It complained that "/usr/lib/openoffice/share/config/soffice.cfg/modules/simpress/accelerator/default.xml/default.xml" is not a directory, and so it was.

There is a double "default.xml" there, the script should have stopped at the first.

So created a folder named "default.xml" in "/usr/lib/openoffice/share/config/soffice.cfg/modules/simpress/accelerator/", and moved the "default.xml" file there.

After this I went for
sudo dpkg --purge --force-remove-reinstreq ooolatex
and this time it complained it cannot find the folder "en-US".

I created that too and copied "default.xml" in there, and finally it worked.

I hope it helps anyone,
Adrian

---

