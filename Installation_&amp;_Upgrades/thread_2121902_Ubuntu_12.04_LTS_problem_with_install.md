---
title: "Ubuntu 12.04 LTS problem with install"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by paulo14d on 2013-03-03
Hello! I have lenovo y580 with win 7 on it. I have created bootable usb(i was using linux live) and set in bios boot from usb option. When there is a time to load system nothing happen, just black window with blinking cursor in left top corner. I was trying to change pendrive, but it didnt help. Someone knows what to do?

---

### Post by darkod on 2013-03-03
First verify if the pendrive works on another computer and that it can boot.

The blinking cursor might be video driver issues. If the laptop has nvidia, you might need the nomodeset parameter to boot in live mode and start the install, and you will also need it to boot into ubuntu once after it's installed. Then when you have booted it first time, you can activate the nvidia driver from Additional Drivers.
ubuntuforums.org/showpost.php?p=10069997&postcount=1

---

### Post by paulo14d on 2013-03-03
I have used it on another netbook, samsung(with nvidia graphics card) with the same result.
I dont know how to set the nomodeset parameter(in the topic you gave, they have written : "[COLOR=#000000]If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom", i dont have purple screen[/COLOR]).

---

### Post by darkod on 2013-03-03
If you don't even get the first purple screen, it might not be created correctly. Try recreating it, best on another ubuntu machine. If creating it on windows use unetbootin or universal usb installer. Sometimes you need to run them with right-click, Run As Administrator so that it has full permissions in win7 to write the boot sector of the pendrive correctly.

---

### Post by paulo14d on 2013-03-03
I dont have acces to machine with ubuntu, i have tried recreating it several times with no results.

---

