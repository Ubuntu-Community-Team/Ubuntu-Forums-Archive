---
title: "Still with the looping bootup"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Duskao on 2009-09-02
Am I the only one still having this issue? I have tried a quite a few different things that I know of try try to fix the problem, but with no avail. I get the new ubuntu art when the OS is starting up, but then it just loops. Again, again and again... I have tried:
sudo apt-get update
sudo apt-get upgrade

They worked, but didn't solve the problem ( I was assuming it was a kernel problem, and it could still be as the kernel hasn't been updated yet)

I tried
sudo apt-get remove xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

Still nothing.

Any thoughts?

---

### Post by taavikko on 2009-09-02
Any chance running ATI GPU?
[http://ubuntuforums.org/showthread.php?t=1250057](http://ubuntuforums.org/showthread.php?t=1250057)

---

### Post by Duskao on 2009-09-02
Yep. Radeon HD 4850.

I am reading through the thread you posted. When my Ubuntu starts up, I don't have a login, I have it set up as auto login, so I think I will have to try to do it from recovery mode. Any advice with that?

---

### Post by taavikko on 2009-09-02
> **Duskao said:**
> Yep. Radeon HD 4850.

Then just follow the link provided.
There's a solution to gain access to desktop once more.

---

### Post by Duskao on 2009-09-02
I am reading through the thread you posted. When my Ubuntu starts up, I don't have a login, I have it set up as auto login, so I think I will have to try to do it from recovery mode. Any advice with that?

---

### Post by taavikko on 2009-09-02
> **Duskao said:**
> I am reading through the thread you posted. When my Ubuntu starts up, I don't have a login, I have it set up as auto login, so I think I will have to try to do it from recovery mode. Any advice with that?

Same thing applies, edit xorg.conf to exclude DRI from loading.
for editor, use nano.

```
Section "Device"
        Identifier      "Configured Video Device"
        Option         "DRI"          "0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Ctrl+o will save
Ctrl+x will exit.
Then restart

---

