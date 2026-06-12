---
title: "The system has reached a state where there are no jobs running."
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by scott_kirkwood on 2006-12-04
I tried doing an upgrade from Dapper to Edgy using the update-manager.
It went on for a while and I would check back on it and it might ask me a question about merging a file.  This went on for several days because it was raining a lot and I was lazy to go to the SOHO to check up on the install. 
The last time I went the monitor was blank and I couldn't get it to wake up.  I tried the mouse keyboard, etc. and eventually did a reboot.
Now if I try to boot (cold or warm boot) my USB keyboard doesn't work.  I plugged in an older keyboard to solve that.
It boots to this:
> The system has reached a state where there are no jobs running.
A shell will be spawned so that you can start such jobs that are necessary.

Type 'exit' when finished.
root@(none):~ #
If I try > echo > file.txt I get > file.txt: Read-only file system.
If I type mount, however, everything starts with (rw..) so I don't know what's wrong there.
Any help you can give would be greatly appreciated.

---

### Post by Thumper322 on 2006-12-04
> **scott_kirkwood said:**
> I tried doing an upgrade from Dapper to Edgy using the update-manager.
It went on for a while and I would check back on it and it might ask me a question about merging a file.  This went on for several days because it was raining a lot and I was lazy to go to the SOHO to check up on the install. 
The last time I went the monitor was blank and I couldn't get it to wake up.  I tried the mouse keyboard, etc. and eventually did a reboot.
Now if I try to boot (cold or warm boot) my USB keyboard doesn't work.  I plugged in an older keyboard to solve that.
It boots to this:

If I try  I get .
If I type mount, however, everything starts with (rw..) so I don't know what's wrong there.
Any help you can give would be greatly appreciated.

Whoa... that doesn't sound too good.

When you turn on your computer, right after your BIOS appears, you should see a message about GRUB. Hit the key mentioned (I think it's Escape), and post what's in your boot menu.

What does **ls /** give you? If you get a normal filesystem, **cd** into **/boot** and tell us what you see...

Good luck!

---

### Post by scott_kirkwood on 2006-12-05
Hi Thumper322,

I tried ESC in the Grub menu and tried booting with various kernels there, both in recovery mode and without.  In every case I get back to the /root prompt below:
> The system has reached a state where there are no jobs running.
A shell will be spawned so that you can start such jobs that are necessary.

Type 'exit' when finished.
root@(none):~ #
My stuff is there, if I cd to /home/scott/ it's all there.  It even mounted my second hard drive.  It appears to mount things read only and almost any command I try has problems (like man command - which complains about not being able to create a tmp file).
What are my next best steps?

---

### Post by Thumper322 on 2006-12-05
> **scott_kirkwood said:**
> Hi Thumper322,

I tried ESC in the Grub menu and tried booting with various kernels there, both in recovery mode and without.  In every case I get back to the /root prompt below:

My stuff is there, if I cd to /home/scott/ it's all there.  It even mounted my second hard drive.  It appears to mount things read only and almost any command I try has problems (like man command - which complains about not being able to create a tmp file).
What are my next best steps?

OK, this is a good sign; you still have all your data. (You might want to back up your stuff, while you still can...)

I Googled the prompt that it gave, you and came across [this page]("http://vivaolinux.com.br/artigos/verArtigo.php?codigo=5748&pagina=3") (translation [here]("http://translate.google.com/translate?hl=en&sl=pt&u=http://vivaolinux.com.br/artigos/verArtigo.php%3Fcodigo%3D5748%26pagina%3D3&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3D%2522a%2Bshell%2Bwill%2Bbe%2Bspawned%26hl%3Den%26lr%3D%26sa%3DG")). 
> [B]# vim /etc/event.d/sulogin
[/B]```

# sulogin - rescue mode
#
on stalled
exec /sbin/sulogin
console owner

start script
        echo
        echo "The system has reached a state where there are no jobs running."
        echo "A shell will be spawned so that you may start such jobs that are"
        echo "necessary."
        echo
        echo "Type 'exit' when finished."
end script
```

I'm not sure what exactly this means; I'm guessing that your system crashed while installing [upstart]("http://upstart.ubuntu.com/") -- the new init daemon.

Try this:
```
fsck /
mount -orw,remount /
```
That'll give you write access to your filesystem.

I'm guessing that you're at runlevel 1; can you **runlevel** to find out, then **cat /etc/inittab**? You can try, say, **init 2** to get to a different runlevel, which might bring up gdm (you *are* using GNOME, right? :p).

Good luck!

---

### Post by raul_ on 2006-12-05
```

fsck

```

Answer "yes" to all the questions. That should do it

---

### Post by scott_kirkwood on 2006-12-06
Backing up will be a little hard, since almost nothing is working :) 
I'll try the 'mount -orw,remount /' first, if that works I can try copying my home to the other drive as insurance.  I have most things backed up in subversion, but there are things that I forget to put there.
Hopefully, fsck will solve all my problems and I can continue the upgrade.  I'll tell you how it goes later.

---

### Post by Thumper322 on 2006-12-06
> **scott_kirkwood said:**
> Backing up will be a little hard, since almost nothing is working :) 
I'll try the 'mount -orw,remount /' first, if that works I can try copying my home to the other drive as insurance.  I have most things backed up in subversion, but there are things that I forget to put there.
Hopefully, fsck will solve all my problems and I can continue the upgrade.  I'll tell you how it goes later.

Try the **mount** and **fsck**, then **init 2**. Good luck...

---

### Post by scott_kirkwood on 2006-12-06
I ran fsck and it basically did nothing, there were no problems.
I don't think this is a disk problem.
mount -orw,renew didn't do anything either.  Complained that it is already mounted or that / is busy, if I remember well. So I still down't know how to make my drive read/write.
I haven't tried init 2 yet.

---

### Post by Thumper322 on 2006-12-06
> **scott_kirkwood said:**
> I ran fsck and it basically did nothing, there were no problems.
I don't think this is a disk problem.
mount -orw,renew didn't do anything either.  Complained that it is already mounted or that / is busy, if I remember well. So I still down't know how to make my drive read/write.
I haven't tried init 2 yet.

**init 2** should bring your computer up normally, but I doubt gdm or kdm will work without a writable filesystem.

Try **umount /**, then the **mount -orw,renew** and **init 2**.

Good luck...

---

### Post by scott_kirkwood on 2006-12-06
> **Thumper322 said:**
> **init 2** should bring your computer up normally, but I doubt gdm or kdm will work without a writable filesystem.

Try **umount /**, then the **mount -orw,renew** and **init 2**.

Good luck...
**umount /** does nothing and shows no output (as if it worked).  
**init 2** also does nothing and shows no output.

I noticed that the command **reboot** would do the same thing, i.e. not reboot and show no output.  **reboot --force** however, does work.

What next?

---

### Post by Thumper322 on 2006-12-06
> **scott_kirkwood said:**
> **umount /** does nothing and shows no output (as if it worked).  
**init 2** also does nothing and shows no output.

I noticed that the command **reboot** would do the same thing, i.e. not reboot and show no output.  **reboot --force** however, does work.

What next?

Yeesh.

Try turning on your computer with no external drives plugged in, then when it's on, plug it in and mount it re-writable. Copy your stuff over manually, and then I suggest reformatting. Looks like that's the only option... Sorry about that. :-k

---

### Post by scott_kirkwood on 2006-12-06
> **Thumper322 said:**
> Yeesh.

Try turning on your computer with no external drives plugged in, then when it's on, plug it in and mount it re-writable. Copy your stuff over manually, and then I suggest reformatting. Looks like that's the only option... Sorry about that. :-k

Ouch, this is becoming the upgrade from hell.
How about if I install with the live CD - the live CD seems to works.
Can I install without overwriting files in my home directory?  Can I reuse my existing user name?
BTW. I don't have any external drives, it's just two big SATA drives.

---

### Post by Thumper322 on 2006-12-07
> **scott_kirkwood said:**
> Ouch, this is becoming the upgrade from hell.
How about if I install with the live CD - the live CD seems to works.
Can I install without overwriting files in my home directory?  Can I reuse my existing user name?
BTW. I don't have any external drives, it's just two big SATA drives.

Oh, d'oh. Can't believe I didn't think of this :roll:. Boot up from the live CD, and everything works? That's your ticket.

So how big is your home folder? I'm assuming everything you need is in there, right? I suggest that you get an external drive (borrow one from a friend, maybe?) or get ahold of some web space, then compress your home directory from the LiveCD and either dump it on a drive or upload it somewhere.

Before you do anything, let me know how big your home folder is; I'll see what I can do about finding you somewhere to store it.

I don't think you can do a clean install and keep your home folder, but I don't know--I'm on my first Linux box.

And doesn't the LiveCD mount internal drives as rewritable?

Good luck...

---

### Post by scott_kirkwood on 2006-12-09
Update:
I've booted the LiveCD opened a shell and mounted my two drives
```
sudo mount /dev/sda1 /old
sudo mount /dev/sdb2 /big
sudo rsync -a /old/home/scott /big
```
Or something like that.  Took a while, I had 63 gigs in my home folder.
The I installed Edgy Eft on /dev/sda1, which didn't have any problems. It formatted the drive and I created the same username as I had before "scott". Then I rsync'd everything back. Wasn't too bad, I still have to reinstall everything, but with synaptic it's easy.

---

