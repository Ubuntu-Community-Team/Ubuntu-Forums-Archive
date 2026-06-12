---
title: "/boot is using 96.9% of 227mb"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by sir_timbit on 2013-02-04
Hi all, hoping someone can help!
I have a web server running Ubuntu 12.04.1 LTS server. As you can see by the title, I'm getting a warning message at logon:
 => /boot is using 96.9% of 227MB

How do I remove the old kernels? uname -r returns 3.2.0_34-generic. I've been searching here and a recommended solution is to do:

```
dpkg --list | grep linux-image
```then

```
sudo apt-get purge linux-image-x.x.x.x-generic
```My problem is when I try to run apt-get purge I get a message about unmet dependencies: eg.

```
sudo apt-get purge linux-image-2.6.38-11-server
```returns...

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.1 is to be installed
 linux-image-server : Depends: linux-image-3.2.0-35-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And the problem is I can't run apt-get -f install because I don't have enough disk space for /boot.

I can see in /boot there are several older versions of initrd.img, config, vmlinuz, etc. I'm a bit leery of just removing these as, based on some of the other posts here, others have tried that and there systems would not successfully reboot.

I'm by no means a Linux or Ubuntu expert so if you have any suggestions, it'd be greatly appreciated. I don't have a GUI installed so no UbuntuTweak.

Thanks,
Sir_Timbit

---

### Post by Bashing-om on 2013-02-04
sir_timbit; Hi !

Here is my tried and true method to remove old kernels, headers and associated files.

If you do not have synaptic installed:
```
sudo apt-get install synaptic
```The command "uname -a" in a terminal will tell you which kernel you are running[which you already know]....then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for "complete removal".
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
Remember to do - in terminal :
```
sudo update-grub
```  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).
[INDENT][INDENT]works for me

[/INDENT][/INDENT]

---

### Post by sir_timbit on 2013-02-04
Thanks for the suggestion Bashing-om! But i don't think I have enough disk space for that to work. When I do:

```
sudo apt-get install synaptic
```I get

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.1 is to be installed
 linux-image-server : Depends: linux-image-3.2.0-35-generic but it is not going to be installed
 synaptic : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.24.0) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Depends: hicolor-icon-theme but it is not going to be installed
            Recommends: gksu but it is not going to be installed or
                        kdebase-bin but it is not going to be installed or
                        policykit-1
            Recommends: libgtk2-perl (>= 1:1.130) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
            Recommends: software-properties-gtk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And I can't run apt-get -f install because it says I don't have enough disk space.

---

### Post by MAFoElffen on 2013-02-04
That's because his recommendation to install Synaptic assumed that you have an xserver, desktop manager and graphical desktop environment, which Server Edition does not.

On Server Edition, you could do the same as he recommended by starting up "aptitude" which is the terminal based package manager in server, thereby letting aptitude check and resolve the dependency issues. Note to other users of Desktop. synaptic and aptitude are no longer installed as default in the Desktop Edition as they slimmed down to the Ubuntu Software Center as a default.

Running server for that long (your referenced kernels), I'm sure you've used aptitude at least a time or few. I use it from the commandline to do what apt-get does, but with more confidence and logic. Safer to do things that way sometimes.

Yes, as I remember, a fresh install only taking about 75MB in /boot...

EDT-- I'm surprised that do-release-upgrade did not remove the old kernels, headers and source. The current upgrade manager usually does this as a default for outdated kernels... (At least I've seen these messages appearing during my release upgrade processes.) Unless you somehow somewhere have it flagged to keep them(?) There is a defaults file for the upgrade manager... but I haven't had need to change mine "much."

---

### Post by Bashing-om on 2013-02-04
@ MAFoElffen Thanks for taking care of my back ! A heartfelt Welcome back !

---

### Post by MAFoElffen on 2013-02-04
Thank you and you are welcome. Great to be back.

Thought I saw this before:
[[SOLVED] Automating removal of old kernels from servers]("http://ubuntuforums.org/showthread.php?t=1961409")

---

### Post by sir_timbit on 2013-02-07
I still appear to be stuck. I tried
```
sudo apt-get remove linux-headers-2.6.38-8 linux-headers-2.6.38-8-server
```but that resulted in:

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubun          tu13.1 is to be installed
 linux-image-server : Depends: linux-image-3.2.0-35-generic but it is not going           to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s          olution).

So that failed. Next, I tried the steps from [URL="http://ubuntuforums.org/showthread.php?t=1402004"]http://ubuntuforums.org/showthread.php?t=1402004
[/URL] ```
sudo mv /boot/*2.6.38-8* /root/boot-backup
```to move and
```
apt-get -f install
```which resulted in the output below.

How do I fix the message
initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.


Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools linux-headers-server linux-image-3.2.0-37-generic
  linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-37-generic
The following packages will be upgraded:
  initramfs-tools linux-headers-server linux-image-server linux-server
4 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
7 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ...
dpkg: warning: files list file for package `linux-image-3.2.0-34-generic' missin          g, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-32-generic' missin          g, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-33-generic' missin g, assuming package has no files currently installed.
(Reading database ... 318866 files and directories currently installed.)
Preparing to replace linux-headers-server 3.2.0.37.44 (using .../linux-headers-s erver_3.2.0.37.45_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Unpacking linux-image-3.2.0-37-generic (from .../linux-image-3.2.0-37-generic_3. 2.0-37.58_amd64.deb) ...
Done.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup erro r from a previous failure.
                          dpkg: dependency problems prevent configuration of ply mouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-server (3.2.0.37.45) ...
No apport report written because the error message indicates its a followup erro r from a previous failure.
                          dpkg: dependency problems prevent configuration of lin ux-image-3.2.0-37-generic:
 linux-image-3.2.0-37-generic depends on initramfs-tools (>= 0.36ubuntu6); howev er:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-37-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-35-generic; however:
  Package linux-image-3.2.0-35-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.35.40); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on plymouth; however:
No apport report written because the error message indicates its a followup erro r from a previous failure.
                          No apport report written because the error message ind icates its a followup error from a previous failure.
                                                    No apport report written bec ause the error message indicates its a followup error from a previous failure.
                                                                              No  apport report written because the error message indicates its a followup error  from a previous failure.
                        No apport report written because the error message indic ates its a followup error from a previous failure.
                                                  No apport report written becau se the error message indicates its a followup error from a previous failure.
                                                                              Pa ckage plymouth is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on mountall; however:
  Package mountall is not configured yet.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 plymouth
 linux-image-3.2.0-37-generic
 linux-image-server
 linux-server
 mountall
 upstart
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1)

Finally, I tried:
```
dpkg --configure -a

```
Which also resulted in:

dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured

---

### Post by sir_timbit on 2013-02-07
Searching on the message:

initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however: Version of initramfs-tools-bin on system is 0.99ubuntu13.1.

brought me to this post, which suggests it's a bug?
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg3974059.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg3974059.html)

---

