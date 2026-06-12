---
title: "After updating computer won't boot"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Incarnadine on 2007-06-05
This is so strange. I just installed Ubuntu  on my desktop computer and the installation went smooth, but after I am done updating my computer and I restart to finalize the updates Ubuntu won't boot anymore. It just freezes on the loading screen. I let it sit there to see what would happen then finally it booted into something called a Busy Cube? I had no idea what that was so I exited and kept trying to boot into Ubuntu, but had no success. So I just re-installed Ubuntu, but didn't upgrade anything because I know I will end up with the same thing. Maybe a driver I am upgrading to isn't compatible? I have no idea what's causing this. Any help would be appreciated. Thanks. As for now I just won't upgrade anything.

---

### Post by wpshooter on 2007-06-05
May I ask what was the version of your Ubuntu ?

---

### Post by Incarnadine on 2007-06-05
I am using the latest version 7.04. I am currently still using my desktop with Ubuntu, but haven't updated anything. I just reinstalled Ubuntu and didn't update anything. Works great like this! Hahahahaha.........things run smooth. It's just I feel dumb that I can't run an update.

---

### Post by wpshooter on 2007-06-05
Well being that it is 7.04 that does not surprise me.

There is probably an update there needs to be fixed.

You might want to wait about a week and try it again.

---

### Post by Incarnadine on 2007-06-05
That's such a bummer. It's like playing russian roulette. Either it works or it doesn't then I'm screwed again and have to reinstall Ubuntu. I hope someone comes up with a solution to this problem. ](*,)

---

### Post by vanadium on 2007-06-05
You were probably the victim of the kernel update. On my desktop system, the update would show the symptoms like you describe. It indeed is worrying and frustrating, especially for a new user who does not have a clue where to start. I am also quite new (made the switch on eastern), but I know already a bit more, and I can confort you that the reinstall is not necessary. However, such things require some experience and being able to get on a forum.

The grub menu lets you boot an older kernel if a newer one does not work. On my desktop, selecting the older kernel started the system as if nothing happened. However, you ask: what&#347; the grub menu? If you did a full install, it probably is hidden: you just get a brief message telling to press the escape key if you want to see the menu.

Here is how to boot your previous kernel automatically instead of the last one:

Using Alt+F2, enter the command

```

gksudo gedit /boot/grub/menu.lst

```

This opens the grub menu in gedit. Scroll dwon quite a bit to the line:
## ## End Default Options ##
Here, the boot options start, with lines such as:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=113d4806-2eb3-492a-bf81-de560d9ed70d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

Yes, that's my 20-16 kernel that seems to work properly on my laptop, but not on my desktop. Comment the whole section out, i.e., put a # at the start of each line. Do the same for the next section, which is for the recovery mode. The next section thus is first seen by grub and will be the default kernel.

---

### Post by Incarnadine on 2007-06-05
Bingo dude! Thanks!!!!!!! You just be promoted to a Exrpesso  Ubuntu user! Hahahaha........thanks for the help. Now I know what to do if this happens again with a future kernal. You the man (or woman)!

---

### Post by lptr on 2007-06-05
anyone having an idea when things will going to be fixed again?

rob*

---

### Post by Incarnadine on 2007-06-07
I wish I knew. I'm just waiting until I get my new update notification and I can update this damn kernal! I don't know if it's the cause, but I notice that somethings just don't work good ever since I installed the new kernal and keep loading up on the older one. The Movie Player plays files ok, but it doesn't do DVD's anymore and I notice that my video card is being held back some how. The screen is choppier and I can't even play Diablo in Wine now. Everything is going down because of this dumb kernal](*,)

---

### Post by Incarnadine on 2007-06-08
Allow me to correct myself because I was a idiot. It's not the kernals fault. I just didn't activate my ATI driver under the "Restricted Drivers Manager". Hahahaha.....go figure it would be something like that. Everything looks smooth now and fine:p

---

