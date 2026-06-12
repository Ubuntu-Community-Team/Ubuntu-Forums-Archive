---
title: "A few issues."
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by Whisper45 on 2008-08-28
I followed all these instructions
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
When I click the by clicking 'this link' download button, it gives me a popup that says: 'cannot find 'wine''. Whats happening?

Also, when I Try to enable 'extra' visual effects, it says 'desktop effects could not be enabled'. I thought this might be because my graphics card driver wasnt enabled. So I goto: System > Administation > Hardware drivers. It says I have none. Now, this morning I have 'nVIDIA graphics driver' disabled. When I tried to enable it it said it couldnt for some reason. Now theres nothing there.
How can I fix this?

Yours,
Whisper.

---

### Post by Cheesehead on 2008-08-28
The painless way to install Wine (and other apps) is through your Add/Remove panel.
Then it will work.

---

### Post by Whisper45 on 2008-08-28
In my add/remove panel, I search 'wine' and nothing comes up.

---

### Post by Whisper45 on 2008-08-28
Now when I click the install wine thing, it says: Install additional software? Press yes.

Can not install Wine E: Unable to correct problems, you have held broken packages

---

### Post by Cheesehead on 2008-08-28
To fix broken packages:
Open a terminal (Accessories -> Terminal) and enter:
```
sudo apt-get -f install
```
The system will prompt you for your password.
Then the system will attempt to fix the broken packages.

If it fails, post the error message.
If it succeeds, go back to Add/Remove and try Wine again.

---

### Post by Crafty Kisses on 2008-08-28
You can also do it through Terminal:
```
sudo apt-get install wine
```

---

### Post by Whisper45 on 2008-08-30
Thanks. Wine is working now. What about the visual effects?

---

### Post by oldos2er on 2008-08-30
Is your video card capable of doing 3d rendering?

---

### Post by Whisper45 on 2008-08-30
It was working before I re-installed ubuntu.
So it has worked with this graphics card before.

---

### Post by Whisper45 on 2008-08-31
No one else has had this happened to them? Isnt there something I can type in terminal or something

---

