---
title: "Upgraded Graphics Card - Cannot boot liveUSB"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by David_Kirba on 2016-04-22
Hello Everyone,

It's been a long time since I visited the forums. I hope you are all doing well.

I have an old IBM ThinkCentre that I use at home as a media centre for my kids. I found a PCI Nvidia card for cheap on eBay and added it to the computer.  The card is a Geforce 6200 with 256 MB of RAM. The computer has 4GB of RAM and a 640 GB SATA hard drive. After adding the card, I got the dreaded blank screen with out of range errors. Rather than try to fix the existing system, I decided to reinstall Xubuntu (15.10) so that it would detect the new hardware during install and then I could take it from there.

However, the live USB pen drive would not boot. Rather, I'm not really sure how far it goes. First I get a grey screen with a white cursor blinking in the top left corner. Then the screen goes blank and the monitor reports there is no signal, so it turns off. All the advice I can find assumes that you get to the installer's first menu, after which you can get it to boot with nomodeset, but I have not been able to get that far. I have looked at the posts on [this thread]("http://ubuntuforums.org/showthread.php?t=1743535"), but the posts there too assume that there is some sort of response from the live USB/CD.

I am considering trying again with a mini ISO, but for the life of me I can't find the new 16.04 version. I know the card works because when the computer starts up, it spits out three lines about Nvidia, then goes to the POST screen with the ThinkCentre logo. I can access BIOS.

Another option I was considering was to remove the card, change video mode to nomodeset (since the original install has not been touched), reinstall the card, and then see what happens. I thought I'd check in here first to see if anyone else had better (less time consuming) advice. I do have two kids running around the house so I'd rather not be opening up the hardware in that environment :)

Thanks for your time!

David

---

### Post by ajgreeny on 2016-04-22
Try booting with the nvidia card still enabled and at the grub menu (hold shift at power on to get the menu if you don't see it normally) then hit "e" when on the boot choice you want to edit the boot options.
Find the line which has "quiet splash" near the end and add nomodeset after those two words, then use F10 to boot.

If that gets you to a GUI we can set the system to use nomodeset always, but you may find that if you now install the recommended proprietary driver from Additional Drivers, that nomodeset is no longer needed.

---

### Post by dckirba on 2016-04-22
Hi ajgreeny,

Thanks for your response. I have tried this with the existing install and I do not get the Grub menu. Instead, I get a prompt that says boot>

This prompt does not accept any bash commands that I know and doesn't offer much help either.

However, I will try it with the live USB as soon as I get home and report back.

Also, I regained access to my old account in case you're wondering why I'm posting as someone else :)

---

### Post by T.J. on 2016-04-22
At a guess, I'd say that we need to look at your BIOS/UEFI settings.  The bootloader is getting as far as it can than dropping to a recovery.

To start, do you use UEFI or a traditional BIOS? Or not sure?

---

### Post by dckirba on 2016-04-22
Hi T.J.,

This is an old IBM ThinkCentre, so traditional BIOS I believe. It does have an option called DVMT that I am not very clear about.

---

