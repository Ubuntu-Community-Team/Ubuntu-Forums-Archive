---
title: "Jaunty Jackalope 9.04 Alpha not working.."
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JakeWatkins on 2008-11-27
I updated my Ubuntu 8.10 to 9.04 using update-manager -d

Now, I have no icons on my desktop, no bottom bar (I had taken the top one out, for closing purposes)

The only reason why I'm writing this, is because my PIDGIN still comes on at first like always, and I had emails, so it opened up Firefox for me.

Alt ` -- Should open up a terminal, but it doesn't.

Is there a way to downgrade back to 8.10?

EDIT: by the way, I can't close Firefox, because there's no real way to get it back opened.. so if someone can help, we'll take it to PM, I'll give credit to who did it, and post the message that fixed it for documentation.

EDIT2: I have a few black dots across my screen at the top, and I logged in on Xubuntu instead of GNOME like I usually do. I have automatic login setup, so I can't stop it from logging on and change to GNOME.

---

### Post by JakeWatkins on 2008-11-27
I really need help, guys, I can't do anything.

---

### Post by JakeWatkins on 2008-11-27
I really just want to save some files, I have 2 flash drives that have 2GB each on them, I can put the pictures and music on them, put them on my Windows machine, and install 8.10 back on this...

Any help?

---

### Post by JakeWatkins on 2008-11-27
How do, using the terminal before boot-up, copy /home/jake/pictures (or the correct place for pictures)

to a USB drive?

---

### Post by adult swim on 2008-11-27
to open firefox or a terminal, push alt+f2 and typen in firefox or gnome-terminal
have you tried booting from a live cd and then trying to backup your stuff?

---

### Post by quazi on 2008-11-27
Do shortcuts still work?  Alt+F2 opens up a run dialog and you can then run gnome-terminal from there.

Alternatively, hit ctrl+alt+f1 and you'll find yourself in a command line interface.  Just attach the usb stick, mount it if necessary, and copy things over.

---

### Post by JakeWatkins on 2008-11-27
Ctrl Alt F1 = success!

Alt F2 = failure.

How do I mount my USB/copy the files over?

---

### Post by quazi on 2008-11-27
I'm writing these commands under the assumption the usb sticks are formatted with fat32.

Stick in the usb stick, then enter
```

cd /dev/disk/by-label
ls

```
and see if it comes up.  If it does, enter
```

sudo mkdir /media/usbflash
sudo mount -t vfat /dev/disk/by-label/##### /media/usbflash

```
where ##### is the usb stikc label.

If the usb stick isn't labeled, you can try guessing what it is by device-id:
```

cd /dev/disk/by-id
ls
sudo mkdir /media/usbflash
sudo mount -t vfat /dev/disk/by-id/############ /media/usbflash

```
where ############# is the device-id (probably pretty long).  Your stick should now be mounted.

Then copy things over with cp:
```
 cp -R /home/jake/pictures /media/usbflash/picbak

```

---

### Post by JakeWatkins on 2008-11-27
```
cp: cannot stat `/home/jake/pictures': No such file or directory
```

...but that is a directory.. it's mine

---

### Post by JakeWatkins on 2008-11-27
and it has a name: it was "/media/JAKEWATKINS" on my Ubuntu before

---

### Post by SoCalChris on 2008-11-27
> **JakeWatkins said:**
> ```
cp: cannot stat `/home/jake/pictures': No such file or directory
```

...but that is a directory.. it's mine

Check the capitalization of the Pictures directory. It defaults to an uppercase P, not the lowercase.

---

### Post by JakeWatkins on 2008-11-28
Will do! (Once I get home).

But, I did find the photos once I popped in a Live CD, but they're protected, and I don't have the permission to copy them over.

Is there any other way I can just... back up? That way I don't lose everything?

Like WoW -- it's like... 11GB I'll have to redownload/install! = (

---

### Post by philinux on 2008-11-28
You do realise, I hope, that Jaunty alpha 1 is for testing purposes only and is liable to break more than once on the way to it's final realease. I would not put this on my main machine. I have it on my second hard drive.

---

### Post by Elfy on 2008-11-28
Can I ask why you have installed the alpha install and not a released one? 

You are likely to get many, many more problems running Jaunty until April next year when it is finally released.

Perosnally I think you might be better of reinstalling Intrepid or if you want a version supported for longer then install Hardy.

Assuming that you have access to either more than 1 cdrom device or external USB devices then you'll be able to backup all that you need to via the livecd.

---

### Post by JakeWatkins on 2008-11-28
> **philinux said:**
> You do realise, I hope, that Jaunty alpha 1 is for testing purposes only and is liable to break more than once on the way to it's final realease. I would not put this on my main machine. I have it on my second hard drive.

Yes, I do realize this, but, I had so much success with 8.10 alpha, that I did not see it as a threat. I know it was dumb to install it without backing stuff up, but, hey, we all do dumb things, right?

---

### Post by JakeWatkins on 2008-11-28
> **forestpixie said:**
> Assuming that you have access to either more than 1 cdrom device or external USB devices then you'll be able to backup all that you need to via the livecd.

The files and folders I need I do not have permission for when I put in the Live CD, is there a way to fix that?

---

### Post by sdowney717 on 2008-11-28
can you use "gksudo nautilus" from a live CD?
this way you become root and can move files.

---

### Post by bodhi.zazen on 2008-11-28
Thread moved.

@Jake: While you are free to test 9.04, as has been pointed out it is in Alpha and you should expect lots of updates (ie bakdwidth) and from time to time breakage.

If you need assistance, please use this subforum (and not "general help").

---

### Post by autocrosser on 2008-11-28
Jake--if you are not easy with fixing your Jaunty--wait til Alpha 4 or 5 to install it--also, I would do it as a SECOND install--that way you have a backup to goto if the testing install breaks (VERY likely!!!). I keep 2 testing installs (had both of them break yesterday!!!) & 1 stable install to go back to if all else fails---I was out of my testing installs for about 2 hours yesterday whilst everyone figured out what went bad with the morning updates----So I suggest you to:

1. Watch the testing forum BEFORE you update to the testing install.

2. Make sure you are comfortable with debugging

3. BACKUP!!!!

4. Backup some more.

5. Expect that the testing install will break AT ANY TIME.

6. If you are not comfortable with this---wait til April.

Early testing is not for the faint of heart.

---

### Post by Gina on 2008-11-28
I second all that.

---

### Post by JakeWatkins on 2008-11-28
So.. "gksudo nautilus" kind of worked.. and by kind of, I mean it didn't.

It took off the permission icon, but I still don't have permission, but I found that if I open a file up, and save it with "Save As" to my flash drive.. it'll save.. but I can't copy/cut because I don't have "reading permissions"

;lakjf;lasjdf;asf

---

### Post by Gina on 2008-11-28
When you're root you can change the permissions. (But you should know that if you're playing with an Alpha)

---

### Post by JakeWatkins on 2008-11-29
Hey guys! So, I popped in a Live CD, and could never get permission! So I went ahead and made a new partition, and installed Ubuntu 8.04 LTS on it. (I'll soon be on 8.10, but no higher!) I installed it with only 1 hitch, which I soon fixed, and I also cleaned up some partitions that were dumb.. taking about 7GB of space, that was rightfully mine!

So I installed it just fine, booted it (it was nice getting back into Ubuntu, that actually worked, kind of... comforting.)

I then tried mounting my 1st partition with all my original files in it. Did it with ease. So I said, OK, let's try accessing them, it asked for my old password, which I knew with ease (this would have been good to ask for before... before I tried 30 times to get the stinking files! Ha!)

Once I verified myself, I had open access to my files! I quickly cut/pasted all my files before my computer changed its mind about things, and now I'm taking that partition down to size, and upgrading my new one to bigger and better things. Ah, the world of Linux. <3

--Jake Watkins

---

### Post by autocrosser on 2008-11-29
Glad you got your problems sorted out--you might wait until the beta is out & just try the LiveCD to see what is going on & I suggest you pop in from time to time to see what we are doing....I started on day one with Jaunty & my system is running top-notch with it. 

I will also suggest if you want to learn more about Linux to dual-boot & install maybe around alpha 4 or 5--the path that Jaunty is on will be fairly well made by that time---alpha 1 is generally for the bleeding-edge people that can debug/fix most anything that goes wrong---and we sometimes need to reinstall to recover from a borked system ;)

---

