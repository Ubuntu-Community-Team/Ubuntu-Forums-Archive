---
title: "Display does not working after upgrade"
date: 2014-06-30
forum: Installation &amp; Upgrades
---

### Post by fredand44 on 2014-06-30
Hello
I think I got Ubuntu 12.x or 13.x, I have not paid enough attention, sorry!
How ever yesterday I checkade my system for uppgrades of installed packages. After uppgrade I got a display problem. I can just log in terminal mode. I tried to run startX but I saw in the output:
Fatal modul nividia_173 not found.
I do not know If this is the problem but I guess it is.
If you know how to solve this please let me know!
Best regards 
Fredrik

---

### Post by slickymaster on 2014-06-30
Try reinstalling the nvidia-173 module:```
sudo apt-get install --reinstall nvidia-173
```and reboot

---

### Post by fredand44 on 2014-06-30
Hello!
I tried it but unfortenately it said:
E: Unable to locate packages nividia_173 
Could I get it some where and reinstall it from a USB?
Or could I at this point keep all contents like files and pictures and install any later version of the Ubuntu Os?
Best regards 
Fredrik

---

### Post by fredand44 on 2014-06-30
Hang on....
Looks like I misspelled nividia_173, Should be, as you said, nividia-173
I Will soon revolt now

---

### Post by grahammechanical on 2014-06-30
Here is something to try. At the Grub menu select Recovery mode. Depending upon the actual version of Ubuntu that you have you may need to open the Advance Options for Ubuntu sub-menu to find recovery mode. A Recovery menu will appear. Select Resume and that should boot using an open source video driver. Once at the desktop you can select a different video driver from the Additional Drivers utility which in 13.10 is found in Software and Updates>Addtional Drivers tab.

By the way, you will need an Internet Connection. Perhaps that was the reason that apt-get could not locate the nvidia 173 package. Or did you mis-type it? nvida-173 or nivida_173. what did you type? I can tell you this, nvidia-173 is in the repositories even of Ubuntu 14.04. So, it should be possible for apt-get to find it.

Regards.

---

### Post by fredand44 on 2014-06-30
Revolt? Where did that come from? 
How ever after the Reboot i still got same problem.
The system is rusning in low-graphics mode...
You Will need to configure there yourself.
But I can not choose that option!!!

Btw Looks I got Ubuntu 12.04.4

---

### Post by fredand44 on 2014-06-30
Hello!
Thanks for the replies!
But how do I efter grub?
Best regards 
Fredrik

---

### Post by fredand44 on 2014-06-30
Sorry for misspelling, I use my telephone with auto-complete.
I ment how do I start grub from terminal?
/Fredrik

---

### Post by fredand44 on 2014-06-30
Btw how can I enable internet access from terminal? Perhaps the nividia_173 driver Will get loaded then.
/Fredrik

---

### Post by slickymaster on 2014-06-30
During the boot press and hold the **left Shift key**. This will bring up the Grub2 menu from where you can select "_Advanced options for Ubuntu_".
[IMG]http://i.stack.imgur.com/01e8n.png[/IMG]
After that you will be able to select the kernel you wish to boot in "_Recovery mode_":
[IMG]http://i.stack.imgur.com/UP5j7.png[/IMG]
This will lead you to the advanced options. By selecting "_Enable networking_" you'll gain access to your network and the internet for upgrades or downloads, and you will also mount your hard drives in read/write mode in case you need to edit files.
[IMG]http://i.stack.imgur.com/fdmNg.png[/IMG]
After the network has loaded, and fielsystems were mounted you will be presented again with the menu, from where you can choose "_Drop to a root shell propmpt_":
[IMG]http://i.stack.imgur.com/tHkmh.png[/IMG]
You are root in this shell. Hence no sudo is needed for administrative tasks. This also means you have full access to all files, and you may cause irreversible damage to your system if you made a mistake.

From the root shell type exit to go back to the menu.

---

### Post by fredand44 on 2014-06-30
Hello!
I managed to enter grub and network, after awhile I got back to the menu, I selected drop to... And then I did the apt-get. it looked like nividia_173 got installed but I hade to accept that it could not get verified.
I took a photo of the output but I can not see how to attached files in this reply???
Then I reboot by write reboot in the terminal. At startup I got back to grub strangely. I then choose the regular kernel.
But the display error remains.
If you guys got any idea please let me know.
Best regards 
Fredrik

---

### Post by slickymaster on 2014-07-01
> **fredand44 said:**
> Hello!
I managed to enter grub and network, after awhile I got back to the menu, I selected drop to... And then I did the apt-get. it looked like nividia_173 got installed but I hade to accept that it could not get verified.
You can check that running the following in a terminal window```
apt-cache policy nvidia-173
```
> **fredand44 said:**
> I took a photo of the output but I can not see how to attached files in this reply???
Click on 'Manage Attachments' which you'll find above the message field. You can upload images that way to the forum and they will appear as clickable thumbnails.
[ATTACH=CONFIG]254377[/ATTACH]

---

### Post by fredand44 on 2014-07-01
Hello again guys!

I got a some help from a friend that the following might help:
apt-get install linux-source
...since source is needed.
And then:
dpkg-reconfigure nvidia-173

How ever it seems like I do not got the correct source for the current kernel, se attached picture.

Do you guys got any ideas?

Best regards
Fredrik

---

### Post by slickymaster on 2014-07-02
Based on your output, it seems that you're lacking the 3.2.0-65-generic kernel headers. At the root shell```
apt-get install kernel-headers-3.2.0-65-generic
```and then afterwards```
dpkg-reconfigure nvidia-173
```should do it.

---

