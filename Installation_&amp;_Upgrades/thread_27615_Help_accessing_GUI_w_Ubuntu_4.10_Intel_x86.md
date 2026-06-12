---
title: "Help accessing GUI w/ Ubuntu 4.10 Intel x86"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by cmay119 on 2005-04-16
Hi all, I've just installed Ubuntu 4.10 Intel x86 Edition on a second partition on my harddrive. I got all the way through the install process, but once it finally asks me for my Username and password to access the OS, I get a message saying:

"I cannot start the X Server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X Server output to diagnose the problem?"

After saying yes to wanting to see the x server output, a new screen pops up saying that there is no user support in this version of linux, and therefore no diagnoses.

After closing the xserver output screen, another message pops up saying:

"I will disable the X server for now. Restart GDM when it is configured correctly".

After this, I can then login but no GUI, only a command line interface.

Can anyone help me setup the GDM so it is configured correctly? Or is that even my problem?

Sorry for the n00b question, this is my first time working with linux. Any help greatly appreciated.

Here are my computer specs:

DFI Lanparty 250GB UT nForce 3 Chipset
AMD Athlon 64 3200+ Socket 754
Seagate Barracuda 120GB SATAII Harddrive
512 MB Kingston Valueram Cas 3
eVGA nVidia 6800 GT AGP 8x
D-Link PCI Wireless Network Adapter 802.11g Model DWL-G510

---

### Post by nad on 2005-04-17
That's a new one to me, "no user support". Here's some support: It seems that the x server did not recognize your graphics' card internel ID. This happens occasionally as the volunteers who write the driver software try to keep up with advancements. But I've never seen that message.

If you would post two files here, either attached or in a code box, they will be reviewed. First, your automatically configured ' /etc/X11/xorg.conf ' file and second ' /var/log/Xorg.0.log '.

By the way, you have not noted your monitor. This could be important also. Thanks for your patience,

Dan M

---

### Post by cmay119 on 2005-04-17
Hi nad, thank you for the reply, but at the command prompt neither of those commands worked? IE they weren't a recognised command. I'm using xfree86 instead of xorg if that makes a difference? 

Here's what the message said, sorry I was so vague with it in the first post. 

"This is a pre-release version of XFree86, and it is not supported in any way." The message than tells me to go to the xorg website and look for help before reporting bugs and whatnot. 


Is there a place I'm suppose to be typing these commands other than the command prompt I'm presented with? I typed both commands like this:

$/etc/x11/xorg.conf
$/var/log/xorg.0.log

Once again thank you for your help.

---

### Post by nad on 2005-04-17
My mistake. 4.10 uses the XFree86 x server. The files we need to look at are, ' /etc/X11/XF86Config-4 ' and second ' /var/log/XF86Free.0.log '. A command to look at the XFree log file in a terminal screen is ' less /var/log/XF86Free.0.log '. This will give you one screenful of output at a time and allow you to scroll through the file.

Since you are posting from a different session, do you have a way to copy these files that we may review them?

Dan M

---

### Post by cmay119 on 2005-04-17
Hi nad, the only way I know, is to right down what I read pretty much word for word.
Would that be acceptable or do you need something more?

BTW: Here is my monitor specs:

19" KDS Flat Screen CRT Model: XF9bi
Max Resolution 1600x1200
Recommended Resolution 1024x768 @ 85 Hz

Horizontal Frequency Range ~ 30-86kHz
Vertical Frequency Range ~ 50-160Hz

---

### Post by cmay119 on 2005-04-17
Okay nad, I just tried what you said. I typed both commands in and neither are a recognized path/file name. Do you have any other suggestions? I'm completely stumped as to what could be the problem. Once again thank you so much for walking me through this, and thank you for your patience. :)

EDIT: Do I need to put the quotes around the commands as well? Is that why the commands are not being recognized?

---

### Post by nad on 2005-04-17
Thanks for the monitor info. You can start by searching these forums for issues with your monitor.

The easiest way for you to copy these files is to a floppy or usb "pen" drive. To copy to a floppy, install the mtools package. The command is ' apt-get install mtools '. Now you can issue the command ' mcopy /var/log/XF86Free.0.log a: ' to copy the file to your a: . If you have a pen drive it could be a little more complicated. When you have inserted the usb device issue the command ' ls /media/sda1 '.  If your hotplug system worked you will see the contents of the pen drive. To copy a file, ' cp /var/log/XF86Free.0.log /media/sda1/. ' . Now issue the ls command again to see if your file is there. If you have no files on the pen drive, the command prompt will simply return. If the ls command returns a no such device error, your pen drive is not mounted. If your pen drive is not auto-mounted, issue the command ' mount -t vfat /dev/sda1 /media/sda1 ' and now the ls command and the cp command. Before you remove the pen drive, issue the unmount command to make certain that the data transfer has been completed. ' umount /media/sda1 '.

I await your results.

Dan M

---

### Post by cmay119 on 2005-04-17
What do I do if ubuntu isn't recognizing the commands that you want me to get. 

Both /etc/X11/XF86Config-4 and less /var/log/XF86Free.0.log came back with the same result:
"Command failed, no such file or path"

Will I still be able to copy the files to a floppy if the command itself cannot be recognized?

---

### Post by nad on 2005-04-17
No, do not include the quotes. Note that the command ' less /var/log/XF86Free.0.log ' is the word less with a space following it then the rest with no spaces. Also note that linux is case sensitive and that that is a zero not a capital O in the filename.

Dan M

---

### Post by cmay119 on 2005-04-17
Okay I'll post back shortly *Crosses fingers and prays*

---

### Post by cmay119 on 2005-04-17
Once again failure. :(

I typed the command "apt-get install mtools" (without quotes) and I get these messages:

"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission Denied)"
"E: Unable to lock the administration directory (/var/lib/dpkg), Are you root?"

I'm unsure on how to log in as "root". 

I'm unsure now what to do.

---

### Post by nad on 2005-04-17
Another mistake on my part. Please use ' less /var/log/XFree86.0.log '. And put the less command in front of the other file name ' less /etc/X11/XF86Config-4 '.

Any results?

Dan M

---

### Post by nad on 2005-04-17
Ahhh... permissions. I'm sorry, another incomplete thought on my part (too much beer with dinner). In order to run apt you will need to issue the sudo command with it, ' sudo apt-get install mtools '. You will be prompted for your password. Enter it and the command should finish.

Dan M

---

### Post by cmay119 on 2005-04-17
[QUOTE=nad]Ahhh... permissions. I'm sorry, another incomplete thought on my part (too much beer with dinner). In order to run apt you will need to issue the sudo command with it, ' sudo apt-get install mtools '. You will be prompted for your password. Enter it and the command should finish.

Dan M[/QUOTE]

Alright nad, I'll give that a try thank you. If this doesn't work, I'm going to give Ubuntu 5.0.4 a try and see if that resolves my issues. Thank you for your help man. I  
really appreciate it. :)

---

### Post by cmay119 on 2005-04-17
SUCCESS!!!! Well nad, I did what you said, but I still couldn't get the XF86 Config to open nor the XF86Free log to open. So I deleted the 4.10 Partitions, and installed Ubuntu 5.0.4 and the GUI works perfectly. Thank you so much for your help. And once again thank you for your patience. :)

---

### Post by nad on 2005-04-17
You are welcome.

Dan M

---

