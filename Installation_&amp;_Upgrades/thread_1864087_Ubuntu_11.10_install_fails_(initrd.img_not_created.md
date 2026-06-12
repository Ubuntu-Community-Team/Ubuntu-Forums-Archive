---
title: "Ubuntu 11.10 install fails (initrd.img not created)"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by dnessett on 2011-10-18
I am attempting to install Ubuntu 11.10 into a clean partition on a multi-boot machine. I chose to format the partition and install the boot loader into it. (I don't really know how to ensure my current mbr isn't changed during the install. I have about 6 OSes currently installed and I don't want to mess with the mbr).

The install gets to the phase where the message "Importing documents and settings" is shown in the progress line. Then the following message is displayed in a separate window:

"An error occurred while migrating data. More details may be found in /var/log/syslog. The installation will continue, but some or all of the documents and settings you requested may not have been transferred to the installed system."

The installation then aborts and the following message displays:

"Installation complete. You need to restart the computer in order to use the new installation."

First, since this is a fresh install, I don't know why the install is trying to migrate data. Second, when I look at /boot in the install partition, vmlinuz-3.0.0-12-generic is there, but initrd.img-3.0.0-12-generic is not. So, there is no way to boot into the new installation. Finally, I looked in /var/log/syslog on the partition by booting into a different Ubuntu installation and mounting the partition. There is no syslog file there.

Does anyone have an idea why this is happening and how I can fix the problem?

---

### Post by sonicb00m on 2011-11-26
I dunno what's going on but I have exactly the same problem. Ubuntu is just getting worse. I had to reinstall because the system got totally ballsed up trying to upgrade the ATI driver.

I am totally tired of it.

---

### Post by alakin on 2011-12-05
dnessett,

I could have written your question word for word! I have experienced exactly the same issue this weekend. Did you ever solve the problem? Is it worth me persevering or giving up now?

---

### Post by dnessett on 2011-12-05
> **alakin said:**
> dnessett,

I could have written your question word for word! I have experienced exactly the same issue this weekend. Did you ever solve the problem? Is it worth me persevering or giving up now?

I gave up and installed 10.4.

---

### Post by alakin on 2011-12-05
> **dnessett said:**
> I gave up and installed 10.4.

I ran the live CD fine and enjoyed playing with unity. I currently use Linux Mint Isadora Xfce and fancied a change. Looks like it is over the Fedora 16 to give the Gnome Shell a go then :lolflag:

---

### Post by kwasibengt on 2011-12-17
hello peeps!

I did also run into this annoying and frustrating error but after some researching
i found a workaround :-)

its seems according to /var/log/syslog (you have to check the filesystem of the installer for the correct one) that their is some trouble with the migration assistant not being able to unmount certain mounts.

you have to boot up a live session of the CD/USB installation and open up a terminal and run these two commands:

sudo -s
ubiquity --no-migration-assistant

now at the first attempt ubiquity did report another error not being able to unmount some other temporary mount.
just quit ubiquity and restart it with the same --no-migration-assistant argument. or you can make sure that all partitions on your harddrive are unmounted before you start ubiquity.
may be its possible to pass the --no-migration-assistant argument at the boot session of the live CD/USB installation but don´t know how to do that at the moment.

migration assistant is needed if you want to migrate documents and settings from other operating systems founded on your harddrive. its weird that we isn´t asked about this one.

now it should install fine on every ubuntu-clone. my fortune was made on lubuntu. enjoy!

/Richard

---

### Post by alakin on 2011-12-18
Hi Richard,

Always good to receive an explanation of why something doesn't work. I looks like the installer would work fine on a clean box with just Ubuntu being installed. I guess the migration assistant comes to life when it sees other OS's and then everything goes wrong!

I have pretty well gone full circle. I have been using xfce for years (on Slackware, Arch, Xubuntu and Linux Mint) but fancied trying out some of this new stuff. I did manage to install Fedora 16 but there was some sort of display/font issue where letters were missing out of words in the menus. It was hit and miss when you clicked on something where you would end up :shock: I have now installed Linux Mint Debian Edition with Xfce. I like the idea of a rolling release based on Debian so I think I will stick with this for now. I must say though that I enjoyed the live experience playing with Unity. Had it installed without any problem I would probably settled there for a while.

Next time that I am ready for a change I'll give it another go :)

Alan

---

### Post by kwasibengt on 2011-12-28
Good to hear alakin!

Well, im pretty much full circle to. slackware, redhat, debian, ubuntu and so on. but i dont like ubuntu anymore. dont like unity, dont like gnome 3. i switched to lubuntu which i based on lxde instead. havnt tried xfce but what i read lxde should be faster. maybe i will try out linux mint debian edition in a vbox just for the fun.

well i had only a previous ubuntu 10.10 install and had only linux on this drive since 2008. so i shouldnt invoke the migration assistant at all.

cheers!

---

### Post by kwasibengt on 2011-12-28
i think this should be reported as a bug.

---

### Post by alakin on 2011-12-29
kwasibengt,

You are right that lubuntu should be quicker, the WM is based on openbox. It is a little too light for me. XFCE is well specced but light enough so as not to get in the way. This means that things like libre office are thrown in as standard.

I have just aquired an old laptop (Thinkpad T42) and needed something fairly light and I have installed Sabayon 7 XFCE. Very nice. A fantastic package management system. It all feels very solid and is now a rolling release distro.

Shame about Ubuntu. Probably my best XFCE experience to date was with Xubuntu several years ago. When the next version came out I had all sorts of problems with graphics. I therefore skipped that release. When the next one came out that also gave me a load of grief so I moved to Linux Mint XFCE. Having tried yet again recently I am becoming tired having expections build up with the live distro only to find that it will not install correctly on my hardware.

That's the great thing about linux - choice.

All the best.

Alan

---

### Post by dnessett on 2012-04-27
This problem also exists in 12.04. Fortunately, the solution give by kwasibengt also works. For the life of me I don't understand why the implementors of the install software can't give us a check box that when selected inhibits the migration assistant. They could even limit the availability of such a check box to the "Do something else" branch, which I presume is intended for those who know what they are doing.

---

