---
title: "Updated today, close lid screen goes to sleep and wont wake up again."
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k3lt01 on 2010-03-12
I updated early this morning, didn't have all the Plymouth troubles others have had at boot up but have come across something else.

Now if I close my laptop lid and the screen goes to sleep when I open the lid again it wont wake up and I have to reboot. I have gone through my power settings and they are all set properly. I have also checked my screen saver settings and they are all turned off so the screen saver shouldn't have an effect.

I find this is more of a nuisance than anything but it shouldn't be like this. Has anyone else found this happening? if yes have you been able to work it out how to fix it yet?

---

### Post by zoomy942 on 2010-03-12
i noticed my hp 5101 doesnt even sleep when i close the lid, but the sleep button works.  lame  ;)

---

### Post by Whitby on 2010-03-27
I installed the Lucid beta a couple of days ago, and it looks like I have the same symptoms.

I normally set the powersave options so that when the laptop lid is closed, the display turns off but nothing else happens, so I can leave the machine running jobs without getting dust settling on the keys.  This works perfectly in Jaunty, and I imagine also in Karmic, but in Lucid when I close the lid, the screen turns off, but won't turn on again when it is opened.  The machine still seems to be running, but there is no way to get the screen back on without turning the machine off and on.

As you said, this an annoyance rather than a showstopper, but it should work.

Machine is a Dell Latitude D630 with onboard intel graphics - a very common corporate laptop in Australia.

---

### Post by k3lt01 on 2010-03-27
I update on the weekends and since last weekends update it has been fine for me. I have no answer as to what was causing it to happen but it is ok for me now. Sorry I can't be of any real assistance.

---

### Post by timosha on 2010-03-27
A dead regression bug which reincarnated in a new body (kernel) ;)

---

### Post by Whitby on 2010-03-27
I did some checking around and found a couple of other posts on this, one of those pointed to a bug on launchpad.  This indicates that the problem was known, and a fix has been rolled out.  This is probably why it now works for you.  

I'm using the lucid beta (fully updated).  Not sure why I don't seem to have this fix.

Anyway, I discovered I can get around the problem by pressing Ctrl-Alt-F1 after the lid is opened.  This goes to the tty1 session, and this turns the screen backlight on again.  Switching back to the graphical session with Ctrl-Alt-F7 allows me to carry on.

I'll keep an eye on this, and see if future updates fix it for me.

---

### Post by praveenmarkandu on 2010-03-27
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058)

i have this bug in karmic

---

### Post by k3lt01 on 2010-03-27
> **Whitby said:**
> I'm using the lucid beta (fully updated).  Not sure why I don't seem to have this fix.Hmmmm, I don't understand that. I updated this morning (about 14 hours ago) and it is still fine today. Unless you updated after I did and a new bug has been introduced in the time between.

> **praveenmarkandu said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058)

i have this bug in karmicBut that bug has nothing to do with my old problem. I don't use, and never have used, suspend or sleep at all.

---

### Post by timosha on 2010-03-27
> **praveenmarkandu said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058)

i have this bug in karmic

I have it in Lucid. But, the bug is only 4 years old and it comes and it goes.

---

### Post by cdEWoozy on 2010-03-27
> **Whitby said:**
> Anyway, I discovered I can get around the problem by pressing Ctrl-Alt-F1 after the lid is opened.  This goes to the tty1 session, and this turns the screen backlight on again.  Switching back to the graphical session with Ctrl-Alt-F7 allows me to carry on.

It was fixed in 2.6.32-15 but reappeared in 2.6.32-16.

[https://bugs.launchpad.net/linux/+bug/540134](https://bugs.launchpad.net/linux/+bug/540134)

---

### Post by timosha on 2010-03-27
> **cdEWoozy said:**
> It was fixed in 2.6.32-15 but reappeared in 2.6.32-16.

[https://bugs.launchpad.net/linux/+bug/540134](https://bugs.launchpad.net/linux/+bug/540134)

And in 2.6.32-17

---

### Post by k3lt01 on 2010-03-27
Well I had it in 2.6.32-15 but haven't had it in 16 or 17.

So I am wondering is it not a kernel bug or are you people posting in the wrong thread. lol.

---

### Post by timosha on 2010-03-27
> **k3lt01 said:**
> Well I had it in 2.6.32-15 but haven't had it in 16 or 17.

So I am wondering is it not a kernel bug or are you people posting in the wrong thread. lol.

Maybe I am posting in the wrong thread LOL. But I am certainly posting in the right launchpad bug thread: [https://bugs.launchpad.net/bugs/44058 ]("https://bugs.launchpad.net/bugs/44058")
take a look at postings #81 and #83 LOL

---

