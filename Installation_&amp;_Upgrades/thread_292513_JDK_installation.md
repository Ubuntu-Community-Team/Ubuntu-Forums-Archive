---
title: "JDK installation"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by CorruptNoob on 2006-11-03
Hi, I've recently installed Ubuntu and been trying to get Java to work. I've downloaded jdk-1_5_0_09-linux-i586.bin and installed it -i think- to my desktop as there's now a folder called jdk1.5.0_09 there.

I don't know how to use it and I don't know why it's there, I'm new at this, I just want to be able to have jdk installed and able to use javac and java commands from the terminal like on apple computers.

I hope you can help me..


thanks.

---

### Post by amohanty on 2006-11-04
Ok:
1. throw out the bin file
2. Do the following:
 - enable the universe repos.
 - **sudo apt-get install sun-java5-jdk**
 - **sudo update-alternatives --config java**
select the sun java and you are good to go.

HTH
AM

---

### Post by CorruptNoob on 2006-11-04
I deleted the bin file from my desktop and entered the first command you listed into the terminal:

shahin@yuki:~$ sudo apt-get install sun-java5-jdk
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
shahin@yuki:~$




Also on my desktop there's a folder named jdk1.5.0_09 and it has a padlock icon to the upper right of it, I can't delete it.

---

### Post by boban on 2006-11-04
Close synaptic / add remove programs first (or another apt installation)

---

### Post by CorruptNoob on 2006-11-04
Only programs I have open (to my knowledge) are Firefox and a Terminal, it says I can't do anything to it because "you do not have permissions to change it or its parent folder."

---

### Post by CorruptNoob on 2006-11-04
It also tells me I'm not the owner of the folder :s

---

### Post by boban on 2006-11-04
Strange... You could try rooting out the problem (eg. check list of processes with ps -A), but I think rebooting is easier solution (after reboot everything should be ok) :)

If you will try to find what is goin on try ps -A from terminal. Search for apt, synaptic or java installation process... Then kill it (sudo kill process_id)

---

### Post by CorruptNoob on 2006-11-04
I've restarted many times during this problen :)


  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  153 ?        00:00:00 pdflush
  154 ?        00:00:00 pdflush
  156 ?        00:00:00 aio/0
  155 ?        00:00:00 kswapd0
  743 ?        00:00:00 kseriod
 1759 ?        00:00:00 ata/0
 1760 ?        00:00:00 ata_hotplug/0
 1763 ?        00:00:00 scsi_eh_0
 1764 ?        00:00:00 scsi_eh_1
 1887 ?        00:00:00 khubd
 1898 ?        00:00:00 khpsbpkt
 1916 ?        00:00:00 knodemgrd_0
 1989 ?        00:00:00 kjournald
 2221 ?        00:00:00 udevd
 3058 ?        00:00:00 shpchpd_event
 3227 ?        00:00:00 dhclient3
 3966 ?        00:00:00 acpid
 4056 ?        00:00:00 syslogd
 4082 ?        00:00:00 dd
 4084 ?        00:00:00 klogd
 4403 ?        00:00:00 gdm
 4419 ?        00:00:00 gdm
 4437 tty7     00:00:52 Xorg
 4446 ?        00:00:00 hpiod
 4450 ?        00:00:00 python
 4497 ?        00:00:00 cupsd
 4522 ?        00:00:00 dbus-daemon
 4537 ?        00:00:01 hald
 4538 ?        00:00:00 hald-runner
 4543 ?        00:00:00 hald-addon-acpi
 4547 ?        00:00:00 hald-addon-keyb
 4549 ?        00:00:00 hald-addon-usb-
 4601 ?        00:00:00 hald-addon-keyb
 4614 ?        00:00:00 hald-addon-stor
 4615 ?        00:00:00 hald-addon-stor
 4617 ?        00:00:00 hald-addon-stor
 4618 ?        00:00:00 hald-addon-stor
 4697 ?        00:00:00 hcid
 4701 ?        00:00:00 sdpd
 4716 ?        00:00:00 krfcommd
 4729 ?        00:00:00 mdadm
 4763 ?        00:00:00 atd
 4776 ?        00:00:00 cron
 4853 tty1     00:00:00 getty
 4854 tty2     00:00:00 getty
 4855 tty3     00:00:00 getty
 4856 tty4     00:00:00 getty
 4857 tty5     00:00:00 getty
 4858 tty6     00:00:00 getty
 4873 ?        00:00:00 x-session-manag
 4915 ?        00:00:00 ssh-agent
 4918 ?        00:00:00 dbus-launch
 4919 ?        00:00:00 dbus-daemon
 4921 ?        00:00:00 gconfd-2
 4924 ?        00:00:00 gnome-keyring-d
 4926 ?        00:00:00 bonobo-activati
 4928 ?        00:00:00 gnome-settings-
 4930 ?        00:00:00 esd
 4938 ?        00:00:04 metacity
 4943 ?        00:00:02 gnome-panel
 4945 ?        00:00:08 nautilus
 4948 ?        00:00:00 gnome-volume-ma
 4956 ?        00:00:00 update-notifier
 4959 ?        00:00:00 gnome-vfs-daemo
 4965 ?        00:00:00 gnome-cups-icon
 4975 ?        00:00:00 trashapplet
 4976 ?        00:00:00 gnome-power-man
 4978 ?        00:00:00 mapping-daemon
 4987 ?        00:00:00 mixer_applet2
 4989 ?        00:00:00 clock-applet
 4995 ?        00:00:00 notification-da
 5005 ?        00:00:00 gnome-screensav
 5031 ?        00:00:23 firefox-bin
 5091 ?        00:00:00 gnome-terminal
 5092 ?        00:00:00 gnome-pty-helpe
 5093 pts/0    00:00:00 bash
 5434 ?        00:00:17 totem
 5446 ?        00:00:00 totem
 5661 pts/0    00:00:00 ps

---

### Post by boban on 2006-11-04
> **CorruptNoob said:**
> It also tells me I'm not the owner of the folder :s
We are talking about java installation folder, right? If so, you can change ownership of folders with chown command (chown user:group folder_name)

---

### Post by CorruptNoob on 2006-11-04
shahin@yuki:~/Desktop$ ls
jdk1.5.0_09
shahin@yuki:~/Desktop$ chown shahin:shahin jdk1.5.0_09
chown: changing ownership of `jdk1.5.0_09': Operation not permitted
shahin@yuki:~/Desktop$

---

### Post by boban on 2006-11-04
ups... forgot to add sudo before it... try

```

sudo chown shahin:shahin jdk1.5.0_09 -R

```

(the -R will change ownership of all subfolders too)

---

### Post by CorruptNoob on 2006-11-04
That worked.. except for now all of its sub-directories are locked! Is there a way to chown a folder AND all its sub-directories?

---

### Post by boban on 2006-11-04
> **CorruptNoob said:**
> That worked.. except for now all of its sub-directories are locked! Is there a way to chown a folder AND all its sub-directories?
-R switch... Forgot to add it... look again at my previous post... :)

---

### Post by CorruptNoob on 2006-11-04
Woo! Deleted that thing, thanks man! Now to install Java and get javac/java working in terminal


edit: that thing is working now: sudo apt-get install sun-java5-jdk it's downloading something :)


edit2: hmm it's downloading sun-java5-demo.. why is it a demo?

---

### Post by boban on 2006-11-04
> **CorruptNoob said:**
> Woo! Deleted that thing, thanks man! Now to install Java and get javac/java working in terminal
You are welcom :)

---

### Post by CorruptNoob on 2006-11-04
Yay it works thanks both people who replied to this thread :)

---

### Post by [D-Tail] on 2006-11-21
Hey CorruptNoob,

I'm browsing these forums as I'm trying to get java 1.5.0_08 working, but I crossed your message about the 'java demo' thing. Java itself isn't a demo, but the jdk package includes some demos (just like on Windows and (I assume) Mac OS). Glad you're helped out, though ^_^

---

### Post by teitunge on 2007-01-23
sudo my friend, sudo :)

---

### Post by Bpa on 2007-12-30
Whenever you see the "Operation not permitted" output, it just means that you have to be superuser or have superuser privileges, To get the command to work, just retype the same command with "sudo" (minus the quotes) in front of it.

---

