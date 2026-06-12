---
title: "Trouble booting ANY linux from USB or CD"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by Underground88 on 2012-01-24
Hello Ubuntu forums! To be quick and to the point... I can't get my E Machine to boot any of my linux live cd's or flash drives. I've had success booting all three(Backtrack 3, Ubuntu 7.04 Live CD's and Backtrack 5 USB) on other machines.


 When I try to boot the Backtrack 5 (usb) on the E Machine I get stuck "ACPI: Power Button [PWRF]" 

 When I try to boot the Backtrack 3 (CD) I get stuck at " * looking for data directory" 

 And finally, when I boot the Ubuntu (CD) I see the Ubuntu logo pop up, and it looks like it's loading, then it flashes back to a screen where it says "can't access tty; job control turned off. (initramfs)" 

I don't have a whole lot of experience with linux distros, but it def seems like it's a problem with the box.. anyone else been through something similar?

Thanks in advance guys.

---

### Post by mastablasta on 2012-01-24
> **Underground88 said:**
>  Ubuntu 7.04 Live CD's  
 
And finally, when I boot the Ubuntu (CD) I see the Ubuntu logo pop up, and it looks like it's loading, then it flashes back to a screen where it says "can't access tty; job control turned off. (initramfs)" 
 
.
 
Ubuntu 7.04 is not supported anymore.
 
Additionally try using latest Ubuntu to get the latest kernel (=drivers) and then post back.

---

### Post by nipunshakya on 2012-01-24
> **Underground88 said:**
> Hello Ubuntu forums! To be quick and to the point... I can't get my E Machine to boot any of my linux live cd's or flash drives. I've had success booting all three(Backtrack 3, Ubuntu 7.04 Live CD's and Backtrack 5 USB) on other machines.


 When I try to boot the Backtrack 5 (usb) on the E Machine I get stuck "ACPI: Power Button [PWRF]" 

 When I try to boot the Backtrack 3 (CD) I get stuck at " * looking for data directory" 

 And finally, when I boot the Ubuntu (CD) I see the Ubuntu logo pop up, and it looks like it's loading, then it flashes back to a screen where it says "can't access tty; job control turned off. (initramfs)" 

I don't have a whole lot of experience with linux distros, but it def seems like it's a problem with the box.. anyone else been through something similar?

Thanks in advance guys.

Hello. First off all warm welcome to the forum.
Regarding your installation stuff, i would suggest you go for latest releases of ubuntu....go for ubuntu 11.04,11.10 or 10.10. U tried to install ubuntu7.04, which i guess is no longer supported for updates.Its been 5 years for 7.04's release. Maybe u should try latest ones.
I guess, sometimes there is issue with the ubuntu you download, and so the installation media would not respond as we want it to.

So its better u download latest ubuntu, make a cd out of the ISO, try the LiveCD session first, check if it works fine, and then go for the installation. Goodluck

Regards,WinuxUser

---

### Post by Underground88 on 2012-01-25
Thank you for the welcome and the replies! (: I was pretty sure that the Ubuntu I had was waay outdated, it was just one that was laying around the office forever. But, back to the problem at hand!

So I downloaded Ubuntu 11.10.. and used Unetbootin to create a bootable usb. I double checked the md5 hash to make sure it matched and it did. Figured I was in the good when I tried to boot, since the normal options screen came up and allowed me to make a choice. I tried to move on and it too freezes at pretty much the same line as Backtrack 5. 

When I tried to select the 'Help' Option it freezes at this screen; 
[http://www.facebook.com/photo.php?fbid=369317346415962&l=6ad5919bed](http://www.facebook.com/photo.php?fbid=369317346415962&l=6ad5919bed)

(I don't have an account on any hosting sites so I just used FB to host *add me and we can be best frands!*) ;P 

It seems that no matter which option I choose it either freezes up before it can start loading, or I get the dreadful 'ACPI: Power Button [PWRF]' message. 

As far as upgrading/downgrading the kernel, since I'm using a Win7 machine to boot, how would I go about doing that? 
[IMG]http://www.facebook.com/photo.php?fbid=369317346415962&l=6ad5919bed[/IMG]

---

### Post by nipunshakya on 2012-01-26
Did you first choose 'try ubuntu' before going with the installation process? 
upgrading kernel meant you do it when u boot to ubuntu or your Unix system. Not possible if you are using win7 machine to boot i guess.
Regarding your error message, i have to admit that i don't understand it...im sorry mate. Probably someone else might help you out with this error...sorry.

Regards,WinuxUser

---

### Post by mastablasta on 2012-01-26
on the first screen after boot (where you can select to try it) there should be some boot options (F6) in the line below the menu. you should try acpi=off option or one of those options. more on these you can read here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Underground88 on 2012-01-26
Thanks a ton guys, the 'acpi=off' command did work actually. After researching for another hour or so lastnight I decided to update my bios drivers and discovered that a lot of e machines are having the same problem. From what I've gathered turning your ACPI off could result in things like cpu fans not working.. so I've kept an eye on it.. seems fine though. Tonight I'll install to my HD and let you guys know how it goes. From what I've read I'll have to edit my grub file to prevent having to add the boot parameter every time I boot.
 
Thanks again guys (:

---

### Post by mastablasta on 2012-01-27
Great!
 
Please mark this thread as solved using thread tools in the top right corner of the thread, so that people with same issue can find the solution.

---

### Post by nipunshakya on 2012-01-27
> **Underground88 said:**
> Thanks a ton guys, the 'acpi=off' command did work actually. After researching for another hour or so lastnight I decided to update my bios drivers and discovered that a lot of e machines are having the same problem. From what I've gathered turning your ACPI off could result in things like cpu fans not working.. so I've kept an eye on it.. seems fine though. Tonight I'll install to my HD and let you guys know how it goes. From what I've read I'll have to edit my grub file to prevent having to add the boot parameter every time I boot.
 
Thanks again guys (:


its good to know about the 'acpi=off' thing....even i'll keep that thing in my mind...
Glad to know your problem was solved....

Regards,WinuxUser

---

