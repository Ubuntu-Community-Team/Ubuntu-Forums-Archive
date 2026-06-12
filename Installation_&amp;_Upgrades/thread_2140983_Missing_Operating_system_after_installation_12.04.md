---
title: "Missing Operating system after installation 12.04"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by viol on 2013-05-01
hello i just installed ubuntu to my pc with dvd, everything was fine, i successfully installed ubuntu and it asked me for reboot and remove the dvd, thats what i did, i removed the dvd and rebooted, and then it says "missing operating system" and nothing happens.. any idea?
thanks in advance

---

### Post by ibjsb4 on 2013-05-01
Are you set to boot (BIOS) from HDD?

---

### Post by darkod on 2013-05-01
Do you have only ubuntu? Some boards do not boot the system if there is no partition with a boot flag on the disk, and since linux doesn't use the boot flag ubuntu doesn't set it.

Boot into live mode with the ubuntu cd, open terminal and post the output of:
```
sudo parted -l
```

---

### Post by viol on 2013-05-01
i had w7 on my pc and i decided to make a dual boot w7 and ubuntu(following a vid on utube) so i installed ubuntu to my secondary disk and it said that it successfully installed and it restarted, when it booted it didnt ask me to choose operating system(w7 or ubuntu) it ran automatically the w7 and they crashed saying a dll file is missing so i format my main disk and put there my ubuntu, and now im getting an error saying "missing operating system"> **darkod said:**
> Do you have only ubuntu? Some boards do not boot the system if there is no partition with a boot flag on the disk, and since linux doesn't use the boot flag ubuntu doesn't set it.

Boot into live mode with the ubuntu cd, open terminal and post the output of:
```
sudo parted -l
```
how can i open terminal, when im running the dvd with ubuntu installation it opens me only the installation

---

### Post by darkod on 2013-05-01
Just click on the ubuntu logo in the Unity interface (first icon) to open the Dashboard, and type terminal in it. It will find it for you. You can search for any program like that.

---

### Post by viol on 2013-05-01
i cant even log to ubuntu to do that, when i boot my pc it loads the motherboard(saying press F12 to enter boot menu etc) and then a black screen saying missing the operating system

---

### Post by darkod on 2013-05-01
If your ubuntu cd/dvd is good, it can't say that. You have to make sure you boot from the cd, not the hdd.

It can say that when booting from hdd only, not from cd.

---

### Post by oldfred on 2013-05-01
Some systems get confused after multiple boot failures. You need a total cold boot or reset which can be difficult with laptops.

 Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by viol on 2013-05-01
and how can i fix it? is it a setting from bios or what?:S

---

### Post by darkod on 2013-05-01
Fix what? oldfred just mentioned some possible problems, it doesn't mean it applies in this case. Lets not think of the worst scenario first.

Before that, are you sure you are booting from the ubutnu cd and not the hdd?
Did you try the cd to boot in another computer to make sure it works?

---

### Post by viol on 2013-05-02
> **oldfred said:**
> Some systems get confused after multiple boot failures. You need a total cold boot or reset which can be difficult with laptops.

 Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)
nothing happend>.>
by the way i just noticed that when i boot the pc and says "missing the operating system" i press turn off button to shut down, and the pc autoboots(im not pressing "restart" button)

---

### Post by oldfred on 2013-05-02
I think that is it just trying to reboot.

If you use one time boot key (f12 on my system) does it show hard drive and CD/DVD as boot choices?

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by viol on 2013-05-03
it auto boot the CD/DVD, btw i redownloaded it again, tried to install it with an external hard disk and i got the same problem

---

### Post by oldfred on 2013-05-03
How are you installing to DVD. Do you have a flash drive, some have better success with them, but some do not?

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

