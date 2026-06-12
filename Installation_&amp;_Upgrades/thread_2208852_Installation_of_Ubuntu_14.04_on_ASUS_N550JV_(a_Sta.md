---
title: "Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by kjano on 2014-03-02
Just FYI to share some good news for those of you considering to buy the ASUS N550JV (I decided to buy the matte display without touchscreen). Before buying a new machine I always check the ubuntu forums for previous reports, so I hope this one will be helpful for some of you guys in the future. 

The forthcoming Ubuntu 14.04 installs without any issues. In the BIOS (F2) you have to enable CSM and disable fast boot.

**Works** (without any modifications):
[LIST]
[*]External SonicMaster subwoofer (!)
[*]Keybord backlight FN keys
[*]Webcam
[*]Wifi
[*]Display brightness
[*]Speaker FN keys
[*]... (In fact, everything I tested so far works)
[/LIST]

**Does not work **(without any modifications):
[LIST]
[*]Display brightness FN keys (any idea how to get them working?)
[/LIST]

**Battery bug**: So far, it seems that I am having no trouble with the battery but other users (of 13.10) report that their battery stopped charging after a kernel update. From what I read, the ASUS BIOS has to be updated. Again, so far I do not have this problem on 14.04 but I will keep checking. My BIOS is version 208.

**Dual boot:** I removed Windows 8 completely so I cannot be of any help if somebody would have questions about dual boot.

**13.10 installation problems:** Installing 13.10 failed numerous times with a 'grub efi amd64 signed failed' message .

---

### Post by Anton_Samarskyy on 2014-04-10
Thank you!
And updates about any other issues?
BTW, does new Ubunut work fine with disk encryption enabled?

---

### Post by den-90 on 2014-04-18
To change display brightness with FN keys you have to modify the file "/etc/default/grub" by adding the string "acpi_osi=" at the end of this line (with root privileges):

[ATTACH=CONFIG]252166[/ATTACH]

Then, type "sudo update-grub" and reboot your computer. After that, changing brightness with FN keys should work!

---

### Post by splater on 2014-04-25
den-90 : confirmed it works for me ! thanks

---

### Post by adrianrosian on 2014-05-04
Works for me too, thank you. I have a problem with the sound in Skype and Viber, though. If I plug in headphones with mic incorporated (smartphone), I cannot get any sound.

---

### Post by roser137 on 2014-05-08
thanks for the tip ! works good on my n550jv too.

---

### Post by geneqew-gmail on 2014-06-08
Thanks [COLOR=#000000]den-90, fn key for brightness [/COLOR]works for me!

As for the battery bug mentioned in the original post, i was able to fix mine by holding the power button for at least 5 seconds during boot (while grub is shown or while option to choose boot options).

For the dual boot with windows 8, grub is able to boot ubuntu but not windows 8. A workaround is to press ESC on boot and manually select windows or ubuntu

---

### Post by riccardo.noc on 2014-06-16
I installed 14.04 too. Same situation. But I have two more problems: 
- Sometimes USB seems not be seen by the system after distro starts.... A simple reboot fix the problem (very annoying) 
- My touch screen does not work properly. Randomly it points on a edge of the screen... I tried to disable it but with no success (using xinput set-prop 'ELAN Touchscreen' 'Device Enabled' 0 )

What about you? What can i do?

---

### Post by ltrevo on 2014-07-24
Anyone know what is the setting for the subwoofer to work properly? My subwoofer is playing together with the right channel.

---

### Post by LK_gandalf_ on 2014-08-25
Hi, thanks for this post, it's great to share this kind of experiences. I just bought a N550JK, and I am going soon to install Linux, probably ubuntu studio or kubuntu. In every case I'll let you know how it will go ;)

---

### Post by Frantic_Earthling on 2014-09-17
> **den-90 said:**
> To change display brightness with FN keys you have to modify the file "/etc/default/grub" by adding the string "acpi_osi=" at the end of this line (with root privileges):

[ATTACH=CONFIG]252166[/ATTACH]

Then, type "sudo update-grub" and reboot your computer. After that, changing brightness with FN keys should work!

Worked for me too.
Many thanks!

---

### Post by murawel on 2014-10-05
Hi there, I had the issues with Fn keys on Asus n550jv.

Approach described on the [page]("http://linux-on-n550.blogspot.com/p/n550jv-issues-and-fixes.html") helped me.
Brightness/Bluetooth/Wifi_on/off works.

How to:
[COLOR=#323232][FONT=Arial]    Modify GRUP parameters (/etc/default/grub)[/FONT][/COLOR]
[COLOR=#323232][FONT=Arial]    Added "acpi_osi=" in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="[/FONT][/COLOR]

---

### Post by thymajesty on 2014-12-13
> **den-90 said:**
> To change display brightness with FN keys you have to modify the file "/etc/default/grub" by adding the string "acpi_osi=" at the end of this line (with root privileges):

[ATTACH=CONFIG]252166[/ATTACH]

Then, type "sudo update-grub" and reboot your computer. After that, changing brightness with FN keys should work!
Men, I love you!!! After tones of scripts and reinstalls it finally works!!!! Thanks))

---

