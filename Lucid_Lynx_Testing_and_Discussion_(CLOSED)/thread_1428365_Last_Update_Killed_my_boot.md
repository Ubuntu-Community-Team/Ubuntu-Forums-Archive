---
title: "Last Update Killed my boot"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TunaCanTommy on 2010-03-12
The last update resulted in a boot failure in both regular boot and  recovery.  I get the following messages:

```
mountall: error while loading shared libraries: libplybootclient.so.2: cannot open shared object file: No such file or directory.
init: mountall main process (265) termiated with status 127
```

I tried a previous kernel to no avail. Everything was going pretty well, up to now!

Any suggestions as to how to fix ? ?

---

### Post by lion1969 on 2010-03-12
Confirm.....  same problem here

---

### Post by Dr. Dexter on 2010-03-12
got the same problem here. It may be possible to boot your PC with a Live-CD and manually but the missing lib file in your filesystem.

[http://home.alessiotreglia.com/lucid/lucid/lib/?order=N](http://home.alessiotreglia.com/lucid/lucid/lib/?order=N) there is your missing one

---

### Post by sgage on 2010-03-12
Same here. No boot. No nothin'

---

### Post by kenden on 2010-03-12
+1, same here.

---

### Post by TunaCanTommy on 2010-03-12
Thanks for chasing down that file.
I'll do what you suggest and respond back.

---

### Post by Rob2687 on 2010-03-12
I think the file name changed. I linked to a similarly named file before rebooting and it went fine.

```
sudo ln -s /lib/libply-boot-client.so.2.0.0 /lib/libplybootclient.so.2
```

---

### Post by Vanishing on 2010-03-12
[http://ubuntuforums.org/showthread.php?t=1428388](http://ubuntuforums.org/showthread.php?t=1428388)

plymouth issue

---

### Post by Dr. Dexter on 2010-03-12
Gracias Rob2687

I'll try this Fix. Sounds a lot better than putting a bunch of different files in my well-tuned-system :D

EDIT_0: thanks it worked.
EDIT_1: there was a new update. Now its safe to upgrade and reboot again.

---

### Post by TunaCanTommy on 2010-03-12
How can I do an update if I can't boot the system ? ?
It locks-up with the OP error message and I can't get to a terminal ? ?

---

### Post by Vanishing on 2010-03-12
> **TunaCanTommy said:**
> How can I do an update if I can't boot the system ? ?
It locks-up with the OP error message and I can't get to a terminal ? ?

you can use a livecd to boot and chroot into your install to update..:popcorn:

---

### Post by Dr. Dexter on 2010-03-12
you have to boot with a live-cd / live-usb

---

### Post by TunaCanTommy on 2010-03-12
Would you mind terribly taking the time to give me a quick "how-to" on 'chroot' to do this. I'd very much appreciate it.

---

### Post by Rob2687 on 2010-03-12
I don't think you need to chroot. Just boot to a liveCD and mount the partition. Then run then symlink the file posted previously. It should be able to boot now.

---

### Post by Vanishing on 2010-03-12
> **TunaCanTommy said:**
> Would you mind terribly taking the time to give me a quick "how-to" on 'chroot' to do this. I'd very much appreciate it.

sure.

check this post:
[http://ubuntuforums.org/showpost.php?p=8071893&postcount=19](http://ubuntuforums.org/showpost.php?p=8071893&postcount=19)

..although you may have to change your directory name a bit..dont run the command with "(change to what you have)", just take it out, its like a comment..lol..am i babbling too much?

edit: why did i forget to add link?

---

### Post by TunaCanTommy on 2010-03-12
@ Vanishing

Did you forget to add the link to the post ? ?

---

### Post by Vanishing on 2010-03-12
> **TunaCanTommy said:**
> @ Vanishing

Did you forget to add the link to the post ? ?

lol...you happened to refresh your browser in the 20 seconds between the original post and the edit...:p

---

### Post by TunaCanTommy on 2010-03-12
I did, my apologies . . . thanks!

---

### Post by kenden on 2010-03-12
Boot using instructions from Steve in the bug report. The easiest is to use a live CD.

then do:
fdisk -l 
(to see your partitions)

sudo mount /dev/sda1 /mnt
(where /dev/sda1 is your boot partition)

sudo chroot /mnt

sudo ln -s /lib/libply-boot-client.so.2.0.0 /lib/libplybootclient.so.2
exit
sudo reboot now


Thanks Rob2687 for the quickfix and Vanishing for finding the bug report.

---

### Post by Vanishing on 2010-03-12
> **TunaCanTommy said:**
> I did, my apologies . . . thanks!

o yea..ignore the mountall deb instructions..:D

---

### Post by keybuk on 2010-03-12
> **kenden said:**
> Boot using instructions from Steve in the bug report. The easiest is to use a live CD.

then do:
fdisk -l 
(to see your partitions)

sudo mount /dev/sda1 /mnt
(where /dev/sda1 is your boot partition)

sudo chroot /mnt

sudo ln -s /lib/libply-boot-client.so.2.0.0 /lib/libplybootclient.so.2
exit
sudo reboot now


Thanks Rob2687 for the quickfix and Vanishing for finding the bug report.

Before you reboot...

mount -o ro,remount /

just in case

---

### Post by TunaCanTommy on 2010-03-12
@Keybuk, Vanishing, Dr. Dexter, Rob2687

Thanks . .  got the system booting again. Sorry for the late response, but I had to take the Missus (She Who Must Be Obeyed) out to dinner.

Did the Live CD boot, mounted the boot partition, did the CHROOT, and changed the symlink.  Worked a wonder . .  rebooted and I'm back in.

BTW - if you boot an older live CD that doesn't recognize EXT4, it won't work.

Great thing about this forum . . excellent help when you need it.

I'll mark this one solved.

---

### Post by Vanishing on 2010-03-12
> **TunaCanTommy said:**
> @Keybuk, Vanishing, Dr. Dexter, Rob2687

Thanks . .  got the system booting again. Sorry for the late response, but I had to take the Missus (She Who Must Be Obeyed) out to dinner.

Did the Live CD boot, mounted the boot partition, did the CHROOT, and changed the symlink.  Worked a wonder . .  rebooted and I'm back in.

BTW - if you boot an older live CD that doesn't recognize EXT4, it won't work.

Great thing about this forum . . excellent help when you need it.

I'll mark this one solved.

oh noes..you betrayed our "alpha testing pride"..
lol..great news(walter bishop tone).

---

### Post by ubuntubrian on 2010-03-15
I've been testing Lucid in VBox and ran into this issue. Any idea how to fix it in there?

---

