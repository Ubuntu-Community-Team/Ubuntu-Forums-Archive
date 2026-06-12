---
title: "seems to be a secret how to unistall ubuntu"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by georgegerm on 2008-10-23
seems to be a secret how to unistall ubuntu
and mainly gru error 17 
the solutions for a beginner like me are way off mark (too hard ) i need 2 pc practically to do this i just what to unistall perion , grub included and maybe reinstall but not now

---

### Post by bettlebrox on 2008-10-23
Microsoft has documentation on how to do this:
[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

Basically all you need to do is [wipe the MBR]("http://support.microsoft.com/kb/69013") (Master Boot Record) to remove the boot loader (for Ubuntu that's grub) and then repartition the drive. You can do this with DOS or a Windows boot disk and use the fdisk command.

---

### Post by pirattrev on 2008-10-23
by 'unistall' do you mean [un]install, or install but a 'u' got in there by accident?  If uninstall use the above link but be warned that _Microsoft is evil_.

_Givens: _
Microsoft = corporation
corporation = money + people
money = sqrt(evil)
time = money
money = people*time; people = money/time

_Proof:_
1. Microsoft = corporation = money + money/time = money + 1
2. (money + 1)^2 = money^2 + 2money + 1
3. Microsoft = evil + 2money + 1
4. money = stock
5. f(economic_crises) = -1/2stock
6. Microsoft = evil + 2(-1/2)) + 1
7. 2(-1/2)) + 1 = 0
8. Microsoft = evil

It's a long proof but it's worth it for the greater good.

---

### Post by linux_tech on 2008-10-23
[http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu](http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu)

---

### Post by steveneddy on 2008-10-23
You don't really uninstall an operating system like an application.

You usually replace the operating system you don't want/like with another operating system with one that you do like and want/need to use.

I suppose that you could format the drive. That would do the trick.

Basically, if you want to install a windows operating system, just put the CD in the drive and restart the 'puter.

---

### Post by Dr Small on 2008-10-23
It's not that it's a secret, just that we hide it deep in the forum :p
You don't need DOS to erase GRUB from the MBR. Just use dd, but be careful!
[http://ubuntuforums.org/showpost.php?p=5081729&postcount=13](http://ubuntuforums.org/showpost.php?p=5081729&postcount=13)

---

### Post by georgegerm on 2008-10-23
> **steveneddy said:**
> You don't really uninstall an operating system like an application.

You usually replace the operating system you don't want/like with another operating system with one that you do like and want/need to use.

I suppose that you could format the drive. That would do the trick.

Basically, if you want to install a windows operating system, just put the CD in the drive and restart the 'puter.

i know i am not the only newbie this has occurred too but i had a great games windows partion before i started using ubu,
and of course to reinstall windows was not an option
so ok i tried partion magic gpart and the windows one from norton till i messed up the whole thing so bad i lost all my games and guess what the ubu partition is still there and now that i had due to lack of knowledge reinstall and loose that great game xp part. now i can and did reinstall windows but it will no show on the screen i have a feeling the disk is gone crazy must go thru the mess of taking it out formatting it externally if i can and star yet again
grub of course was the main issue as it did not want to see other partions i had made (!) as far as i know wincrap could take up to 4
well needless to say i am not happy but learning 
i am writting this on my old pc were only ubus son linux mint is running but to do all again on my fast pc is going to be a big pain
and trust me i can read i have a degree,,
but it is not as simple as it should be and second for newbies like me i know know i should have left the game pc alone with wincrap
ps. the advice i received gratefully and free was at times so different i did not know what to choose or use ,,, trial and error
yet i knew what i was getting into, but happy camper you cannot call me:guitar:
i am not giving just changing my ways so man can say thus he has learned, and learned and will not stop learning

---

### Post by theduffman on 2008-10-24
uninstall ubuntu , as in remove the partitions and bootloader? with windows installed already ?
boot into windows, disk management util (right click my computer/Manage) then delete the ubuntu/swap partitions.
reboot with windows install disc in drive, boot from it, press R when prompted, choose which partition windows is on (1 by default)
enter password if any and type fixmbr
then exit. remove cd

---

### Post by estyles on 2008-10-24
Doesn't seem to be a "big secret" when there's a big thread on it in the Tutorials and Tips Section: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Also, I can understand if English is your second language, but some capitalization, punctuation, and paragraphs might make it possible to read and maybe even understand your posts.

---

### Post by georgegerm on 2008-10-26
> **estyles said:**
> Doesn't seem to be a "big secret" when there's a big thread on it in the Tutorials and Tips Section: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Also, I can understand if English is your second language, but some capitalization, punctuation, and paragraphs might make it possible to read and maybe even understand your posts.

sorry doing my best
as an add on this in the end went and tried to do as written.
then i ecided to try instead of xp for games simply ubuntu 64
well my luck now i have a blank screen and no bios 
either the ram mainboard or gcard went down
now im not a bad loser but as odd as it seems this are the facts the card ram and or mainboard must be relaced and they are expensive here in germany so i am messed up
if any one has an idea thanks
i cannot replace as i have only and older pc with linux mint and is not a compatible to my new one with the old one ram ddr2 to ddr,,
normal agp slot etc. so i cannot transfer things to check whats is bad, so ill have to wait till i get a lot of mulla again,, the cgcard alone was 215 euro, which for me is a lot, and the repair or check here goes into about 60 euro so ill take donations LOL
man what a screw up
iwish i had left it alone
and for the love of me why it was a 6 month old made to order pc ocz dual ram, asus p5n sli board, xfx 8800gt nvidia gcard  etc. good parts all around, why would they go bad on a reinstall?? my luck
and no i wont go to the trouble of sending it back with garantie here it takes a loong time, and it is a mayor pain but i may have no choice
thanks to anyone with a new idea:guitar:

---

