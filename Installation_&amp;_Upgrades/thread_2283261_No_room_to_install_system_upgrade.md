---
title: "No room to install system upgrade"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by Bob_Bornfrend on 2015-06-20
I am trying to install latest version from 14.04.2 LTS. It requires 107.7 MB to download but Software Updater says there's not enough free disk space. I tried emptying trash and removing temporary packages to no avail. I have a 40 GB disk with 35 GB free but Disk Manager indicates only 255 MB is assigned to Partition 1 FileSystem. How can I increase this partition size so I can install the latest versions? Thanks.
PS: I tried to free up space by using sudo apt-get autoremove. That didn't work so I manually tried to delete old kernels (-24 & -37) but I get knocked out for not having permission. I don't understand why not, since I created the installation to have admin rights. I can't seem to change permissions, either.

---

### Post by deadflowr on 2015-06-20
Post the output for 
```
df -h
```
and to double check to make sure the inodes aren't used up
```
df -i
```
Most likely you have a separate boot partition which needs to be cleaned regularly because new kernel image are placed there, and while the system should have a mechanism in place to clean it automatically it doesn't always work right.

---

### Post by Bob_Bornfrend on 2015-06-20
Sorry, I get no response running df -h

---

### Post by Bob_Bornfrend on 2015-06-20
Sorry, I get no response running df -h or df -t
You are right that the boot partition is too small (255 MB). So I tried navigating to the /boot folder but I can't delete anything (permission denied) even though I am classified as  Administrator. If I could delete the 3 previous versions of initrd.img, config, and system.map I could free up 85.7 MB.

It would be nice also to be able to increase the size of the boot partition to avoid future issues. I have the room. Isn't this possible? I have another computer I converted to the same Linux version and it has a 160 GB HDD where Partition 1 (Bootable) = 159 GB, Part. 2 (Extended) = 1.1 GB, and Part. 5 (Swap) = 1.1 GB. I have no idea why the install on the other one created such a small bootable partition.

---

### Post by grahammechanical on 2015-06-20
Some commands need to have sudo as a prefix and that will set up a prompt for our password. Otherwise we are simply told that we need to be root.

Regards.

---

### Post by Bob_Bornfrend on 2015-06-20
sudo df -h  or -t don't give any response either, nor a request for password.

---

### Post by ajgreeny on 2015-06-20
Something is obviously very wrong if you don't get any response to the df commands.

Lets see first what kernels you have installed at the moment and then we can try to remove them as best we can, though it may not be as simple as it should normally be.  In terminal run command ```
ls /boot | grep vmlinuz
```

Can we also ask why you have a separate /boot partition; is it because you have used LVM or encryption?  If you use neither of those separate /boot partitions seem to often cause the problem you are seeing.

---

### Post by deadflowr on 2015-06-20
It's [FONT=times new roman]I[/FONT], small-case I, -i;  not T, -t.
But, more hmm.
Odd, overall, odd.
df wouldn't need sudo, so no need to run that.
However the outlook for admin rights seems peculiar.
what does
```
id
```
say?
(that is a small I, for the record)

---

### Post by Bob_Bornfrend on 2015-06-20
I'm not getting any response from that command either, but I know from looking at the /boot folder I do have previous kernels 3.13.0-24, 37, & 49. (Current version is 14.04.2 LTS) You may be onto something with the encryption comment. I vaguely remember being asked that when I installed the OS.

---

### Post by bapoumba on 2015-06-20
Sorry to ask, do you try these commands from a terminal ?

---

### Post by Bob_Bornfrend on 2015-06-20
I'm not sure I understand your question. I'm entering the commands using the keyboard; the computer is a laptop.

---

### Post by deadflowr on 2015-06-20
The terminal refers to a program called Terminal.
If that helps.
It's a program like any other program, such as firefox.

---

### Post by bapoumba on 2015-06-20
Please hit CTRL-ALT-t at the same time (I hope that is the proper shortcut, not using regular ubuntu here) and that will open a terminal window. Enter df -h then paste the output here. Then run df -i and paste the output here again.

---

### Post by Bob_Bornfrend on 2015-06-20
I'm not sure I understand your question. I'm using the keyboard on my laptop.

---

### Post by Bashing-om on 2015-06-20
Bob_Bornfrend; Hello; I try and help.

We are trying to get you to a terminal. Let us "assume" that you have a standard desktop install of ubuntu, such that the desktop environmebt you have is unity.
Now in unity from the booted desk top if you do the key combo ctl+alt+t (control key AND alt key held down and while these keys are held down also press the 't' key) on your desktop will appear the application "terminal".
On this terminal type the requested commands:
```

df -h
df -i

```
one command at a time . 'df -h' and press the enter key. You see in that terminal the results of the command:
Now copy and paste the results back here - within code tags - .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Now if you are unable to comply, and you have followed directions and still can not get a terminal in the unity interface, the situation is hopeless and all you can do is salvage your personal data, and (RE-)install the operating system. None of us think this is the case !

[INDENT][INDENT]this too is a process of learning
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-06-20
> **Bob_Bornfrend said:**
> I'm not sure I understand your question. I'm using the keyboard on my laptop.
But typing the command into where using the keyboard?

The terminal we speak of is just an  empty (dark purple usually) box with a command prompt showing in the format of **username@hostname:~$**

You just type **df -h** or whatever, and hit enter.

---

### Post by Bob_Bornfrend on 2015-06-20
Oh, I understand now you want me in Terminal mode. Thanks for the CTL-ALT-t sequence. 
I can't copy-paste easily because I'm using a second computer to talk to you, but I think the relevant info you want is for /dev/sdal (Type ext2) which reports Size=236M, Used=151M, Avail=73M, and 68% usage mounted on /boot. That's the core of my problem since the updater needs a minimum of 106M to install the update. There's another 9% used on /home/bobborn/.Private (Type ecryptfs), and another 9% on /dev/mapper/lubuntu--vg-root (Type ext4) but the main problem is the small size of the boot partition.

I tried manually deleting the file initrd.img-3.13.0-24 and others from previous versions, but I get an error message saying I don't have permission even though I have Administrator privileges. Perhaps the folders are encrypted (?) preventing me from accessing the files, but other than logging in I don't see any option to get to the system folder. I've been using the File Manager PCManFM that came with the OS to navigate to the root directory. That's where Delete doesn't work.

---

### Post by bapoumba on 2015-06-21
From a terminal window, please run :
```
uname -r
```
That will tell you which kernel you are currently running
```
dpkg --list | grep linux-image
```
That will tell you all the installed kernels.

The idea is to remove all BUT the current running kernel (for obvious reasons) and the previous one (in case something happens to the current one). Kernels are labelled with sequential numbers, so keep the one from the first command and the previous one.

To remove kernels, as I gather you are running lubuntu : [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
You also can do it from synaptic if you have it already installed : [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Bob_Bornfrend on 2015-06-21
Thanks for the link to RemoveOldKernels. What did the trick for me was to use UXTerm to enter the command "sudo apt-get autoremove linux-image-3.13.0-xx-generic" where xx is the old version number. I had tried that command before, but without the linux-image prefix.

I'm still bugged by the small boot partition that was originally created. It seems strange that Linux wouldn't provide any easy way to resize partitions.

---

### Post by bapoumba on 2015-06-21
There is a whole series of bugs, latest one here : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
You can add a "me too"..

For now, the important thing to do is to keep an eye on the new kernel upgrades and do the housecleaning on a regular basis. Glad to see you fixed it :)

---

### Post by ian-weisser on 2015-06-21
> **Bob_Bornfrend said:**
> I'm still bugged by the small boot partition that was originally created. It seems strange that Linux wouldn't provide any easy way to resize partitions.

Ubuntu has many easy ways to resize ordinary partitions.
However, when you decided to use encryption or LVM during the install, you told the system to not use ordinary partitions anymore. Those tools (like 'parted', which is part of Ubuntu's default install) don't work with encrypted disks nor LVM.



> **bapoumba said:**
> There is a whole series of bugs, latest one here : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
You can add a "me too"..

By 'me too', bapoumba *doesn't* mean a comment. Unhelpful comments make a bug reports confusing and harder to triage.
A 'me too' (I'm sure he meant after seeing many of his threads) means clicking the "*Does this bug affect you?*" link at the top of the bug report.

---

### Post by Bob_Bornfrend on 2015-06-21
I really appreciate your help. Thanks again.  ):P

As an FYI to others who might search on this thread, I've concluded that you can't delete individual files such as initrd.img-3.13.0-24-generic because it's part of the kernel package. That's why I kept getting a "Permission Denied" message. Only by using the command listed above can the whole package be removed.

---

### Post by Bashing-om on 2015-06-21
Bob_Bornfrend; Yeah

In large part. The package management system exist for a reason. Going behind the package manager's back:
> 
delete individual files such as initrd.img-3.13.0-24-generic

real bad things can result.

Keep life simple and do whatever it takes to keep the package manager happy. 'dpkg' keeps things in the family .

[INDENT][INDENT]just my 4 pounds worth
[/INDENT][/INDENT]

---

### Post by bapoumba on 2015-06-22
Sorry, yes ian-weisser, this is what I was meaning :)

---

### Post by marco-stella2 on 2015-06-22
I think I have the same problem and this is what is prompted when I use commands df -h and df -i:


/dev/mapper/ubuntu--vg-root  455G   63G    370G  15% /
none                         4,0K     0    4,0K   0% /sys/fs/cgroup
udev                         1,9G  4,0K    1,9G   1% /dev
tmpfs                        376M  1,3M    374M   1% /run
none                         5,0M     0    5,0M   0% /run/lock
none                         1,9G  188K    1,9G   1% /run/shm
none                         100M   68K    100M   1% /run/user
/dev/sda1                    236M  191M     33M  86% /boot


/dev/mapper/ubuntu--vg-root 30261248 397030 29864218    2% /
none                          480240      2   480238    1% /sys/fs/cgroup
udev                          477465    537   476928    1% /dev
tmpfs                         480240    583   479657    1% /run
none                          480240      4   480236    1% /run/lock
none                          480240      8   480232    1% /run/shm
none                          480240     33   480207    1% /run/user
/dev/sda1                      62248    328    61920    1% /boot

---

### Post by Bashing-om on 2015-06-22
marco-stella2; Hello;

This:
> 
/dev/sda1 236M 191M [color=red]33M[/color] 86% /boot

says you do not have room to install any additional kernels. Have you tried the simpler direct solution ?
```

sudo apt-get autoremove

```
to free up the disk space .

Then see what results:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
to see if the new kernel installs .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

