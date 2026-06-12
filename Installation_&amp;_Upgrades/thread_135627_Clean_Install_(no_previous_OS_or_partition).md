---
title: "Clean Install (no previous OS or partition)"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by greenmaji on 2006-02-24
Im having trouble finding information about exactly what has to be on the hardrive before installation can begin.

Ive searched google and google groups and didn't understand what I'm missing.

I opened an old fedora core 3 CD to see the diffence in the ISO of it and ubuntu.. Fedora Core has a autorun to get the hardrive formated.. Im guessing this isn't the case with ubuntu.

I dont have a OS on the computer in question. It doesn't have a grub or mbr.
Im not quite sure were to begin to get the instalation CD to work. I would think that adding a auto run file to the CD would work if there was a partion manager or a boot loader included but Im not sure if thats the case.

I think Im making this far mor difficult then it is..

---

### Post by taurus on 2006-02-24
You don't have to have anything on the HD first before you install Ubuntu.  Insert Ubuntu CD into the drive and boot from it.  Then at the prompt, just hit enter and follow the instructions on the screen...  The installer should find everything on your system and either auto partition your HD or you can use an expert mode and do the partitioning yourself.  It's real easy to install.  ;)

---

### Post by bluevoodoo1 on 2006-02-24
When I installed  breezy on this computer the hard drive had NOTHING on it, no grub, no mbr no OS, nothing. All the formatting and partitioning was done with the breezy install disc. 

To get the CD to work you have to hit one of the F* keys to be able to boot from your CD drive. Mine is F8 and my old computer was F11. You have to hit one of these right after your restart your computer. 

NOTE: You DON'T have to go into BIOS and switch the order of booting devices, what I'm talking about is a separate event. Check your motherboard's or computer manufacturer's website (or manual).

---

### Post by greenmaji on 2006-02-24
Thats odd. I can't get the CD to boot. It gives me a "No Operating System Found" message when I try to boot from the CD. Live CD's and CD's with autorun files boot just fine. This one is having issues.

And I did go into the bio's to make sure the CD dirve was the first priorty to boot quite some time ago.

It is good to know that I shouldn't have to do manual formating though.

The bio's on this computer are odd, they have options for what operating system your running and DOS extended memory (or not) that Im not used to.
The settings have notes about UNIX so Im guessing that Linux want in mind (Ive tryed setting it to the UNIX settings and it doesn't want to do anything so there goes that idea)

---

### Post by lcg on 2006-02-24
[QUOTE=greenmaji]Thats odd. I can't get the CD to boot. It gives me a "No Operating System Found" message when I try to boot from the CD.[/QUOTE]
Actually, that probably is a message from the boot loader on your harddisk, which is started once the BIOS tried the CD an couldn't boot from it. You should see the same message without a CD in the drive.

[QUOTE=greenmaji]Live CD's and CD's with autorun files boot just fine. This one is having issues.[/QUOTE]
If other CDs boot fine, then I strongly suggest you try to boot this CD at a different computer. ;)

BTW, autorun and bootable CDs are two completely different things.

HTH,
Lars

---

### Post by greenmaji on 2006-02-24
[QUOTE=lcg]If other CDs boot fine, then I strongly suggest you try to boot this CD at a different computer. ;) [/QUOTE]

Well.. that answers that question.
No, the CD doesnt boot up on a diffent computer.

Its the 5.10 install iso.. do you have to do something to it to get it to be bootable?

---

### Post by J77 on 2006-02-24
Did you burn the CD as a 'bootable CD'? :-k

---

### Post by greenmaji on 2006-02-24
to the best of my knolege, yes

any details exactly how this is done (just in case I didn't do something I should have)

---

### Post by J77 on 2006-02-24
In Nero - you have to go into the advanced settings to burn it as bootable cd (or dvd).

When you get your initial splash screen - go into the boot menu thing (F12) and put boot into CD as the first priority.

If it still doesn't boot into the CD then its maybe not bootable...

---

### Post by greenmaji on 2006-02-24
I honestly thought I did that (Ive done it for most of my distro's anyway) but I seem to remember just opening the ISO with winrar and burning them with one of the distro's and since this one isnt working right now I would venture to guess this is it.

Im copying the iso over to the comptuer that has a CD burner now.. Ill re-burn it later today..

thanks for the help so far everyone :P

---

### Post by Coelocanth on 2006-02-24
Make sure you burn it at low speed. 8x is good, 4x is better. I've read if you burn it too fast it will often not boot.

---

### Post by lcg on 2006-02-24
[QUOTE=greenmaji]Its the 5.10 install iso.. do you have to do something to it to get it to be bootable?[/QUOTE]
No, there is nothing special about it. Just open your favourite burning program and burn the ISO as an image.
Important: If you create a bootable CD and just add the ISO file, it will **not** work! The ISO file already is a bootable CD and just needs to be burnt bit by bit (pun intended) exactly as it is.

Oh, and two more things:
[LIST=1]
[*]Before you burn the CD again, download the MD5SUM and check the ISO file to make sure it was downloaded correctly
[*]CD-RW are pretty useful for such tests ;)
[/LIST]

HTH,
Lars

---

### Post by lcg on 2006-02-24
[QUOTE=Coelocanth]Make sure you burn it at low speed. 8x is good, 4x is better. I've read if you burn it too fast it will often not boot.[/QUOTE]
If you really need to burn that slow to get a readable result, you should probably get a new burner or some better quality media. ;)

Lars

---

### Post by lcg on 2006-02-24
[QUOTE=J77]In Nero - you have to go into the advanced settings to burn it as bootable cd (or dvd).[/QUOTE]
Sorry, but that is wrong. You only have to mess with the bootable CD settings if you want to create your own bootable CD, the ISO file is an image so you just burn it as one.

Lars

---

### Post by Coelocanth on 2006-02-24
[QUOTE=lcg]If you really need to burn that slow to get a readable result, you should probably get a new burner or some better quality media. ;)

Lars[/QUOTE]

One would think that, yes. However, when cruising these boards while researching about Ubuntu, the sheer number of posts about the CD ISO needing to be burned slow in order to work properly would lead one to conclude otherwise. I read a number of posts where people were having problems with the burned CD. Many of them were cleared up by burning at slow speeds. I have my doubts they all needed better quality media or a new burner. *shrug* Perhaps so, though.

---

### Post by lcg on 2006-02-24
[QUOTE=Coelocanth]I read a number of posts where people were having problems with the burned CD. Many of them were cleared up by burning at slow speeds. I have my doubts they all needed better quality media or a new burner. *shrug* Perhaps so, though.[/QUOTE]
Though the problems were solved by burning at slower speeds, there may still have been other reasons why the first disc did not work.
Usually, I burn at the maximum speed both the burner and the medium support, because that is what the medium was made for. And, of course, because I am an impatient guy. :)

However, I have burnt a fair amount of CDs and DVDs myself during the last years (all at the maximum supported speed, some even faster) and all of them worked without problems. There were a few incidents when the box locked up while burning and the medium was hosed, but that is to be expected in that case. :)
I do, however, follow the manufacturer's recommendation on what types and brands of media to use. They hopefully know best what works on their hardware and what doesn't.

Lars

---

### Post by greenmaji on 2006-02-24
good greef I feel kinda dumb.

Well.. Its working.. :D

I did use Nero and I used the Burning ROM tool and clicked on the data CD icon then the ISO tab and off I went burning it at 48X ,that was the only choice for speed anyway, I have to use the DVD burner to drop down to 8X but the media is rated for 52X so it works fine.

thanks again everyone. :D

---

### Post by greenmaji on 2006-02-25
Small update.
Im posting this from the Ubuntu system!!! \\:D/ 

all is well so far..
I just need to spend a little time on this system to figure out how to change change things and speed things up a bit. I'll start digging around for information soon on that.

and thanks again. :p

---

