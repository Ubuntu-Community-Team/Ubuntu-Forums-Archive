---
title: "Unable to install software or upgrade"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by morpheus73 on 2011-09-29
Hello, I just downloaded and installed 11.04 on an IBM Thinkpad T42. Previously I was using 9.04 on a dual boot with windows xp pro. Windows quit working for some reason so I thought I'd just remove it and the old linux distro and install a fresh up to date copy of linux. The install went fine but when I try to update or install software using software center, synaptic or terminal it fails to complete. 

For example, using synaptic to install abiword this is the error msg I get:

Extracting templates from package: 100%
Preconfiguring packages...
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

No matter what program I use to install any software program, whether it be synaptic, terminal or software center this is the error message that I always get, every time. I have tried everything that I have found in this forum for command line codes and nothing has worked.

I have even tried to upgrade to 11.10 and that didn't work either. Please, does anyone here have any ideas? Thank you very much in advance.  :)

---

### Post by dino99 on 2011-09-30
boot in recovery mode (hold "shift" key down at bios end process to get the grub menu, then select the 2d line) and select "repair packages"

---

### Post by morpheus73 on 2011-09-30
Thank you for the quick reply. I did what you suggested and it looks like I am getting numerous errors and then it said it was checking the disk and it had errors, hit f to fix, i to ignore, m for manual recovery etc. So I hit f to fix, it took a long time with lots of errors such as [249.665097  ] {DRDY error} then it finally went to the grub menu. I then selected reapir packages and then it said Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool;main/l/lightdm](http://us.archive.ubuntu.com/ubuntu/pool;main/l/lightdm) etc. etc. Apparently it failed to fetch files from many different archives similar to the above address. The last error message stated E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Finished, please press ENTER

SO I hit enter and it returned to the grub menu. I then selected to boot into file system check, it rebooted to the first menu where I select recovery mode or normal. Then I selected normal and it did a disk drive check. Then it booted into the normal desktop.

I then selected a terminal and typed in sudo apt-get update --fix-missing. Before that I had to enable the wireless network. I then typed in apt-get install abiword, it downloaded the files then gave me the error message again that I showed in my first post.

Then I went into ubuntu software center and tried to install 7zip and it gave me the exact same error message as my first post. I'm sure I'm screwing up somehow here, but being a noob Im not sure what the problem is?

So, in addition to what I tried above, I have also tried reinstalling 11.04, and every time I try to install anything using terminal, synaptic or software center, I am still getting the 'start-stop-daemon' error as I mentioned in my first post. Does anyone have any ideas as to what I can try? Thank you all very much in advance for your ideas. :)

---

### Post by morpheus73 on 2011-10-02
So, in addition to what I have already tried, I just ran ubuntu 11.04 from the usb pen drive and then used software center to install spider solitaire and it worked just fine. So now I am trying to reinstall ubuntu from the icon on the desktop. I selected the option to delete the previous install and start fresh using the entire hard drive instead of making separate partitions.

Does anyone feel that this is not the best way to install? Thank you for your time and expertise. :)

---

### Post by morpheus73 on 2011-10-02
Well, after numerous attempts at reinstalling, I keep getting ata1.00 {DRDY ERR} errors during boot. And it will no longer boot into the desktop. So I think that my hard drive is toast, after searching these issues on the net. Is this correct? Does anyone have any other ideas or am I dinked? Thank you for your time.

---

