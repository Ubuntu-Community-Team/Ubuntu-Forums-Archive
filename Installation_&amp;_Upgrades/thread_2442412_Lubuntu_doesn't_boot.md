---
title: "Lubuntu doesn't boot"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by dg95 on 2020-05-03
Hello everyone,

i have installed lubuntu 19.10 on a Toshiba Satellite c660-21z and chose the option to delete the hard drive.
Now it doesn't boot into lubuntu. I have run the recommended option of the boot-repair tool but it seems that there was an error.

Here is the boot repair summary: [https://paste.ubuntu.com/p/Fj9nZCj8t5/](https://paste.ubuntu.com/p/Fj9nZCj8t5/) 

Can anyone help me? 

Thanks and kind regards,
Daniel

---

### Post by VMC on 2020-05-03
I'm not seeing a efi partition. It did come with Windows, yes?
Why Lubuntu 19.10, Lubuntu 20.04 LTS is out. 19.10 will be EOL soon.

Is this installed in mbr mode?

---

### Post by yancek on 2020-05-03
You have a Legacy install of Lubuntu (line 159 of boot repair) on /dev/sdc, the Hitachi 298 GB drive.  Have you tried setting this drive to first boot priority in the BIOS?
Line 184 shows Grub installing to the MBR of that device (sdc) and the standard Grub files are shown for that OS install on the / (root filesystem) parttion, sdc1.

---

