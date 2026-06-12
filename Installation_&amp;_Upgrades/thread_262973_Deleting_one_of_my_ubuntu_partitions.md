---
title: "Deleting one of my ubuntu partitions?"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Old Pink on 2006-09-22
Hi, 

I have two Ubuntu partitions as a result of a huge error I had to fix, but anyway, back to the situation: 

I've had two ubuntu partitions before, and last time I deleted the uneeded one, I got a GRUB "Error 22" prompt. 

I don't want this to happen again, but I need the partition deleted. As last time I had Error 22 I fixed it by reinstalling another Ubuntu partition, I think grub is on the partition I need to remove, and will therefore cause another 22 if I do delete it. 

So basically:
How do I delete one of my Ubuntu partitions, leaving another ubuntu partition along with XP WITHOUT any errors? :-&

---

### Post by wieman01 on 2006-09-22
Show us a screenshot of GParted and we'll see what we can do. Can you do that?

---

### Post by Old Pink on 2006-09-22
Here:

[ [IMG]http://www.filehive.com/files/0922/Th.Screenshot.png[/IMG]](http://www.filehive.com/i.php?i=0922/Screenshot.png)

I want hda4 deleted. I'll then resize hda2 to 10GB.

hda1 = XP Professional to keep
hda2 = Ubuntu to keep
hda3/5 = Swap partition to keep
hda4 = Ubuntu to be removed

---

### Post by wieman01 on 2006-09-22
Je... This is a bit small. Can you post a bigger version please?

---

### Post by Old Pink on 2006-09-22
Click it to enlarge, lol. :P

---

### Post by Old Pink on 2006-09-22
What if I go in the partition I want to delete, copy all of the /boot folder into the partition I want to keep, edit menu.lst to remove the partitions I want to delete and then boot the live cd to delete the partitions? 

I don't fully understand *why* I got error 22, and why deleting a partition creates an error?

---

### Post by wieman01 on 2006-09-22
I enlarged it but see for youself. Cannot recognize much...

---

### Post by wieman01 on 2006-09-22
Not sure what's wrong with the pic, but it's either you or me... ;-)

---

### Post by Old Pink on 2006-09-22
Due to a lack of replies here, I deleted the partition. 

I haven't rebooted yet, what do I do before rebooting?

[B]Edit:
[/B]Big picture: [http://www.filehive.com/files/0922/Screenshot.png](http://www.filehive.com/files/0922/Screenshot.png)
How do I delete and re-install grub?

---

### Post by Henry Rayker on 2006-09-22
pic is plenty big for me, so I think it might be you.

Also, I have deleted partitions in the past with no error 22...so I'm not sure what caused yours. I've deleted Ubuntu partitions 3 times now.

---

### Post by wieman01 on 2006-09-22
The problem may lie in your "/etc/fstab" file... It still points to the deleted partition.

---

### Post by Old Pink on 2006-09-22
Hmm... do I dare reboot?

---

### Post by wieman01 on 2006-09-22
If you showed me your fstab file plus A LARGER VERSION OF YOUR IMAGE... I could tell just that. ;-)

---

### Post by Old Pink on 2006-09-22
[quote=wiemannn01]If you showed me your fstab file plus A LARGER VERSION OF YOUR IMAGE... I could tell just that ;)[/quote]
Ok wieman, attached below are:
[LIST=1]
[*]The original image your system couldn't see
[*]The fstab saved as a .txt file
[*]The CURRENT/RECENT gparted screenshot.[/LIST]Do your magic, wieman!

---

### Post by Old Pink on 2006-09-22
> **wieman01 said:**
> The problem may lie in your "/etc/fstab" file... It still points to the deleted partition.

Actually I think it lay in "the deleted partition was the one that had grub stage 2" in it. 

Now the one I want to keep had it in too, but it was pointing at the wrong one? ???

---

### Post by wieman01 on 2006-09-22
In my opinion it's safe to restart. But just to be 100% sure... Could you also post:
> /boot/grub/menu.lst

---

### Post by wieman01 on 2006-09-22
Oh oh... There may be a problem. SWAP is on the extended bit of you HD. But only the primaries are listed in "fstab". Cannot remember if that is right.

Could you create a new SWAP partition next to "hda2"? Then post the latest screenshot and we adjust "fstab". Just to play safe, mate.

---

### Post by Old Pink on 2006-09-22
menu.lst (in .txt format) and device.map(.txt) attached below. 

My swap has always been extended, and I've never had a problem... 

Doesn't ubuntu mount swap upon startup? :?:

---

### Post by Old Pink on 2006-09-22
So... am I good to go?

---

### Post by wieman01 on 2006-09-22
Sorry, Matt. I feel asleep because I saw you went offline. Different timezone here. I reckon everything went fine? Can you give me a quick update?

BTW: You posted the wrong file... I was asking for "/boot/grub/menu.lst" but I cannot find it.

---

