---
title: "unable to open files list file for package `mktemp'"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by lawtech on 2008-06-19
The following error worries me. mktemp is important. What does this mean, and how do I fix it? This is the first time I've seen an error from synaptic.

From synaptic, I tried to install kpovmodeler. I got the following:

E: /var/cache/apt/archives/kpovmodeler_4%3a3.5.8-0ubuntu1_i386.deb: unable to open files list file for package `mktemp'

In the details:

(Reading database ... dpkg: error processing /var/cache/apt/archives/kpovmodeler_4%3a3.5.8-0ubuntu1_i386.deb (--unpack):
 unable to open files list file for package `mktemp': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/kpovmodeler_4%3a3.5.8-0ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

<no further text>

My installation:

uname -a:
Linux black-host 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

cat /etc/issue:
Ubuntu 7.10 \n \l

---

### Post by lawtech on 2008-06-28
Just to close this out, I got it "fixed."

Somehow /var/lib/dpkg/info/ lost some files. The mktemp.list file was missing entirely. I managed to recover it from a backup, and that got me past the error message I reported. However, another one cropped up immediately. It turned out the offending package was also missing its .list file. On closer inspection, there were dozens of them missing .list.

I tried various apt-get check, clean, etc., all of which appeared to run fine. But the issue remained.

Since I was running gutsy and had intended to upgrade to hardy anyway, I did a fresh install of hardy in that partition.

Guess what? The problem is gone.

No idea what caused the original problem. Hope it doesn't recur. Thoughts from anyone would be interesting.

---

### Post by katalyst23 on 2008-09-30
I have a similar problem.  I get the error message **unable to open files list file for package `libxklavier11'**, though I checked /var/lib/dpkg/info and libxklavier11.list was still there.  Has anyone else come across this problem and found a solution? I really don't want to have to reinstall.

---

### Post by katalyst23 on 2008-10-01
So, I tried reinstalling synaptic hoping it might be able to fix the problem.  No dice, instead I got these error messages : 

```
 sudo apt-get install --reinstall synaptic
[sudo] password for katlyn-kun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgoffice-0-common emacs21-common xserver-xorg-video-amd libdns32
  libpt-1.10.10-plugins-alsa libpt-1.10.10 emacs21-bin-common libopal-2.2
  xaw3dg
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1302kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main synaptic 0.61ubuntu9 [1302kB]
Fetched 1302kB in 3s (344kB/s)     
(Reading database ... 
dpkg: serious warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `binfmt-support' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xsane-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gedit' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxvmc1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-fusion-plugins-extra' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libfribidi0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-netstatus-applet' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gdata' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-tdfx' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ubuntu-wallpapers' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `myspell-en-za' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgraphviz4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnomevfs2-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmagick10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `aptitude' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `psutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgtkhtml2-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `notification-daemon' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgphoto2-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-apt' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/synaptic_0.61ubuntu9_i386.deb (--unpack):
 unable to open files list file for package `libxklavier11': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/synaptic_0.61ubuntu9_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I just recently did a fsck which found and fixed a lot of errors on my harddrive, I think in the process it might have made these files disappear and corrupted the libxklavier.list file.  Is there anyway to get around this or replace the files?

---

### Post by katalyst23 on 2008-10-01
I fixed my problem! Not sure I feel really comfortable with my solution, but I can install packages again.  

Since I had no idea how to generate a .list file by hand (it looks like it lists where all the parts of the application were installed, am I right about that?), and there were quite a few, I cheated and just did ```
sudo touch filename.list
```.  This got me past those errors and then I had to delete libxklavier11.list (I couldn't open or copy it anywhere at all) and recreate it using touch. After this I had a few more random packages that didn't have their list file, so I created the files using touch and now I can install things just fine.  I didn't have to reinstall synaptic at all.  

I do have one more question though.. am I right in thinking that since the real .list files are gone, those packages weren't properly uninstalled and still have related files floating around in the file system?

---

