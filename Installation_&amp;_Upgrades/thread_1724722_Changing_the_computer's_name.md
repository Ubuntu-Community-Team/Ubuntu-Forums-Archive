---
title: "Changing the computer's name"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Bill Grabowski on 2011-04-08
I've installed Ubuntu 10.10 in a separate partition next to WinXP in the hope that I could use Ubuntu as a **printer server** for my network hooked to computers using WinXP, Vista, and Win 7, and another computer with a WUBI installation of Ubuntu 10.10.

Everything works except ... I can't get the other computers to see the Canon MP830 printer on the network. I've loaded the printer successfully as a local printer on my server, and the other Ubuntu computer sees the Ubuntu printer server, but not the printer. I've set the printer settings to share and changed Samba config to browse, share, etc. I suspect that the name for the computer that was selected is too long and this may be causing problems (the name is "bill-Dimension-8250". On other computers this appears either as  "bill-Dimension-" or "bill-Dimension-8". 

I cannot find a way to change the name of the computer from "bill-Dimension-8250" to something shorter and simpler, like "Dell". Any suggestions?

Bill

---

### Post by Dutch70 on 2011-04-08
I'm sure this isn't the only way, but you can change it with Ubuntu Tweak. It's in software center.

---

### Post by CharlesA on 2011-04-08
You can edit /etc/hostname

```
sudo nano /etc/hostname
```

Also, you'll need to change the name in the /etc/hosts file too.

---

### Post by Bill Grabowski on 2011-04-08
> **CharlesA said:**
> You can edit /etc/hostname

```
sudo nano /etc/hostname
```

Also, you'll need to change the name in the /etc/hosts file too.

Thanks Charles! That did the trick. Simple two edits and name for my computer is now "Dell". 

Dutch70: Thanks for tip, but the Tweak I found in the Ubuntu Software Library was a hex editor, and it wasn't clear to me what to hex.

As far as the printer is concerned, at first I still couldn't find the printer on the network, so I ate dinner, came back, and tried again. Voila! Printer seen on networked Ubuntu computer. Now... to check those Windows machines ... If I can get it to work on my wife's Vista laptop, I'm going to sneak Ubuntu 11.4 onto her computer. 

Love the quick and effective response. Thank you.

Bill

---

### Post by Bill Grabowski on 2011-04-11
One other thing I should add. I found the program **Ubuntu Tweak** that Dutch70 mentioned after finding a web site for it at [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) after reading about it in _Beginning Ubuntu Linux, Fifth Edition_. This is a great program and I'm surprised it isn't included within the distribution.

After downloading and installing it, open it by selecting "Applications / System Tools / Ubuntu Tweak" from the top menu bar. Move down the left pane in _Ubuntu Tweak_ to "System", under which is "Computer Details", then the first item under "System Information" in the right window is "Hostname", and to the right of this is an action button labeled "Change Hostname." 

Pretty simple and convenient!

Bill

---

### Post by Dutch70 on 2011-04-11
Nice, glad you like it. 

I believe the reason it doesn't come out of the box is to keep the size down, so that it will fit on a cd, I'm not sure about that.

It does come in the repo's though, and is as easy to add as opening a terminal and running...
```
sudo apt-get install ubuntu-tweak
```

The only downside is, it's not very well known yet, but it's getting there and who knows, may be included soon.

---

