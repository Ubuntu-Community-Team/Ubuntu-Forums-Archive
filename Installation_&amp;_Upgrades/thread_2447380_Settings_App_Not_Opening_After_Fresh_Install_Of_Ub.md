---
title: "Settings App Not Opening After Fresh Install Of Ubuntu 20.04"
date: 2020-07-17
forum: Installation &amp; Upgrades
---

### Post by dkc.com on 2020-07-17
Hi Friends,

On Dell XPS
Did a fresh install of Ubuntu 20.04 (Dual Boot Windows 10)

Settings app hasn't opened even once after installation.
I tried [this]("https://askubuntu.com/questions/1237965/reporting-i-cant-open-settings-in-ubuntu-20-04-lts") but it didn't help.

I am crippled without the Settings App GUI.

Any solutions?

---

### Post by tea for one on 2020-07-17
What is the error message when you try to open the Settings via the terminal?

```
gnome-control-center
```

Please post the output in code tags.

---

### Post by dkc.com on 2020-07-18
Sorry mate, can't paste anything in code bcz there weren't any. But, when I took the screen shot, It captured the following:

[IMG]https://imgur.com/Xh2dz6p[/IMG]

It means the GUI is opening but I am unable to reach there. (I tired ctrl + alt + up arrow key / down arrow key) but there were nothing visible on any workspaces.

Is there any other ways?

[ATTACH=CONFIG]286485[/ATTACH]

---

### Post by ActionParsnip on 2020-07-18
Is the OS fully updated?
If you make a fresh Ubuntu user, does it happen if you log in as that user rather than your first user?

---

### Post by tea for one on 2020-07-18
Do you have more than one display attached?

---

### Post by dkc.com on 2020-07-19
Yes, the OS is fully updated through 'Software Updates' and it is a fresh install.

I can't create a new user because the settings app is not accessible and I don't know any other workaround to create a user.

---

### Post by dkc.com on 2020-07-19
> **tea for one said:**
> Do you have more than one display attached?

No additional displays. Just the laptop screen.

---

### Post by tea for one on 2020-07-19
> **dkc.com said:**
> No additional displays. Just the laptop screen.

I&#8217;m still puzzled by your screenshot in post 3 where two displays are detailed:-

Built -In Display 1366 x 768 
Unknown Display

Anyway, as a suggestion, I would remove all external devices (usb sticks, cameras, headphones, printers etc) and boot into the recovery mode.

Grub menu > Advanced options > Recovery mode > Repair broken packages.

Possibly, during recovery mode, there may be other info/warnings?

Worth a shot?

---

### Post by tea for one on 2020-07-19
> **dkc.com said:**
> Yes, the OS is fully updated through 'Software Updates' and it is a fresh install.

I can't create a new user because the settings app is not accessible and I don't know any other workaround to create a user.

You can add a new user via the terminal.

Here are the instructions - scroll down to the end of the page.

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by dkc.com on 2020-07-19
> **tea for one said:**
> I’m still puzzled by your screenshot in post 3 where two displays are detailed:-

Built -In Display 1366 x 768 
Unknown Display

Anyway, as a suggestion, I would remove all external devices (usb sticks, cameras, headphones, printers etc) and boot into the recovery mode.

Grub menu > Advanced options > Recovery mode > Repair broken packages.

Possibly, during recovery mode, there may be other info/warnings?

Worth a shot?

I thought it was a workspace which I can't access.
Will try the Grub option and let you know the results.

---

### Post by dkc.com on 2020-07-19
> **tea for one said:**
> You can add a new user via the terminal.

Here are the instructions - scroll down to the end of the page.

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Thanks will try that too.

---

### Post by tea for one on 2020-07-19
> **dkc.com said:**
> I thought it was a workspace which I can't access.
Will try the Grub option and let you know the results.

For information about workspaces

Help(Ubuntu Desktop Guide) > Your Desktop > Windows and workspaces > Working with workspaces

---

### Post by icarus-j1149 on 2021-06-07
> [COLOR=#000000]I&#8217;m still puzzled by your screenshot in post 3 where two displays are detailed:-[/COLOR]

[COLOR=#000000]Built -In Display 1366 x 768[/COLOR]
[COLOR=#000000]Unknown Display[/COLOR]

[COLOR=#000000]Anyway, as a suggestion, I would remove all external devices (usb sticks, cameras, headphones, printers etc) and boot into the recovery mode.[/COLOR]

[COLOR=#000000]Grub menu > Advanced options > Recovery mode > Repair broken packages.[/COLOR]

[COLOR=#000000]Possibly, during recovery mode, there may be other info/warnings?[/COLOR]

[COLOR=#000000]Worth a shot?[/COLOR]

Thank you! This one worked for me on ubuntu 20.04.

---

