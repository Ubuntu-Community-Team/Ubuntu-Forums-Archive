---
title: "Dual Booting Windows and Ubuntu on separate hard drives"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by humulos on 2011-08-25
Good day all. I have been messing around with the ubuntu family for some time now, and usually have no problem finding my answers. This one, however, is giving me some trouble.

I have been using ubuntu on my laptop for some time now, and recently got a new 2TB hard drive for my desktop. I cloned the old hard drive to the new one, and decided to install ubuntu onto a third drive. The third drive was IDE, the new one is SATA. I disconnected the other hard drive, and so my current set up is a SATA drive with Windows 7, and an IDE drive with Ubuntu (11.04 of course)

Well, I am unable to dual boot between the two, unfortunately, and would like to figure out how. I would like to say the problem is with Windows, since that is the primary drive. No GRUB shows up upon booting when both drives are plugged in, and the Windows Bootloader does not show my installation of Ubuntu, instead it goes right to Windows. 

Any ideas? Please ask me for any clarification.

---

### Post by Basher101 on 2011-08-25
This is a controller issue (i think not 100% sure tho). Your BIOS can only handle one at a time for boot

---

### Post by ottosykora on 2011-08-26
is the ide drive set to 'cable select' or manually to slave? 

it seems to be mandatory that ide drives today are set to CS.

is it classical MBR setup? 
If you boot the computer from life cd, and run gparted, do you see both drives there?

Where was the bootmanager (grub or other) installed to? Or are you using the w7 bootmanger ?

---

### Post by ottosykora on 2011-08-26
is the ide drive set to 'cable select' or manually to slave? 

it seems to be mandatory that ide drives today are set to CS.

is it classical MBR setup? 
If you boot the computer from life cd, and run gparted, do you see both drives there?

Where was the bootmanager (grub or other) installed to? Or are you using the w7 bootmanger ?

---

### Post by oldfred on 2011-08-26
Many BIOS promote an IDE drive to sda, then windows is not sda and has trobles since it has settings for drive0.

Best to post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

