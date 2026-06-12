---
title: "error i don't understand"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by rdeeds on 2012-10-14
i am new to linux. i just installed lubuntu and am having an error. 


```
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
(Reading database ... 137563 files and directories currently installed.)
Preparing to replace libjavascriptcoregtk-1.0-0 1.8.0-0ubuntu2 (using .../libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libjavascriptcoregtk-1.0-0 ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libjavascriptcoregtk-1.0.so.0.13.2'
Errors were encountered while processing:
 /var/cache/apt/archives/libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libwebkitgtk-1.0-0:
 libwebkitgtk-1.0-0 depends on libjavascriptcoregtk-1.0-0 (= 1.8.1-0ubuntu0.12.04.1); however:
  Version of libjavascriptcoregtk-1.0-0 on system is 1.8.0-0ubuntu2.
dpkg: error processing libwebkitgtk-1.0-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwebkitgtk-1.0-0


```
that is what it says. i attempted both the synaptic method of resolution and apt-get install -f neither worked. can anyone help?

---

### Post by marinara on 2012-10-14
what and where did the error come from?

---

### Post by rdeeds on 2012-10-15
the error came from updating packages. i removed osmo and i could update again but any time i try to update the javascript engine library it says failed using the GNU to update.

---

### Post by rdeeds on 2012-10-16
is there anyone who can help me? i wanted to download libre office and it won't let me because of the javascript core.

---

### Post by drpjkurian on 2012-10-16
pleae ensure that libgtk2-perl is installed. Let me know that. You can check this in synaptic package manager. Please install synaptic package manager if it is not installed and check the status of libgtk2-perl. If this package is not installed please install this by using synaptic package manager

---

### Post by rdeeds on 2012-10-16
it was not installed. i installed it and tried to upgrade my libjavascriptcoregtk-1.0-0 again and it still did not work.

---

### Post by rdeeds on 2012-10-16
installArchives() failed: E: Read error - read (5: Input/output error)
E: Error reading archive member header
E: Prior errors apply to /var/cache/apt/archives/libpurple0_1%%3a2.10.3-0ubuntu1.1_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Read error - read (5: Input/output error)
E: Error reading archive member header
E: Prior errors apply to /var/cache/apt/archives/libpurple0_1%%3a2.10.3-0ubuntu1.1_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Read error - read (5: Input/output error)
E: Error reading archive member header
E: Prior errors apply to /var/cache/apt/archives/libpurple0_1%%3a2.10.3-0ubuntu1.1_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 146667 files and directories currently installed.)
Preparing to replace libjavascriptcoregtk-1.0-0 1.8.0-0ubuntu2 (using .../libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libjavascriptcoregtk-1.0-0 ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libjavascriptcoregtk-1.0.so.0.13.2'
No apport report written because MaxReports is reached already
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
dpkg-deb: error: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libpurple0_1%%3a2.10.3-0ubuntu1.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libjavascriptcoregtk-1.0-0_1.8.1-0ubuntu0.12.04.1_i386.deb
 /var/cache/apt/archives/libpurple0_1%%3a2.10.3-0ubuntu1.1_i386.deb
Error in function: 

is what came up.

---

### Post by jerrrys on 2012-10-16
try this

sudo apt-get clean

sudo apt-get update

---

### Post by rdeeds on 2012-10-16
and what does that do? i have never seen the sudo apt-get clean command before. i did it, and it a bunch of stuff showed up. lol. but it worked. thank you!

---

### Post by jerrrys on 2012-10-16
#7

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

and

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and  

welcome to the forums  :)

---

