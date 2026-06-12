---
title: "Open Office Problem"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yasasflash on 2010-02-02
Hey guys,

After doing some "partial Upgrade" which offered by the update manager, my Open Office seems to be unavailable now. when i launch any open office application, the splash screen shows up and the progress bar is progressing to the end, but then nothing happens.
Splash screen remains forever. 
Can you give me some help about this issue.  :-(

---

### Post by yasasflash on 2010-02-02
I am using Karmic kola alpha2

---

### Post by VMC on 2010-02-02
> **yasasflash said:**
> I am using Karmic kola alpha2

Open konsole and type 'ooffice' and see if any error messages come up.

---

### Post by yasasflash on 2010-02-02
When i do that it opens the open office window but none of the buttons are working. And no error messages shown in the console.
Open office freezes and even it doesn't close when i press Ctrl+c in the console.

---

### Post by xebian on 2010-02-02
> **yasasflash said:**
> I am using [COLOR="Red"]Karmic[/COLOR] kola [COLOR="red"]alpha2[/COLOR]

You realize it's still alpha so a lot of problems.

Strongly suggest you get the[COLOR="red"] Karmic Koala Final[/COLOR].

---

### Post by yasasflash on 2010-02-02
> **xebian said:**
> You realize it's still alpha so a lot of problems.

Strongly suggest you get the[COLOR=red] Karmic Koala Final[/COLOR].
yeah man i get the point. But the thing is i'm in the middle of some heavy work load soo can't waste time to install ubuntu again. so i thought there may be some solution  available for this issue.

---

### Post by xebian on 2010-02-02
> **yasasflash said:**
> yeah man i get the point. But the thing is i'm in the middle of some heavy work load soo can't waste time to install ubuntu again. so i thought there may be some solution  available for this issue.

Good luck.

---

### Post by Merk42 on 2010-02-02
> **xebian said:**
> You realize it's still alpha so a lot of problems.

Strongly suggest you get the[COLOR="red"] Karmic Koala Final[/COLOR].

Um, which came out in October.

yasasflash, you're using **Lucid Lynx Alpha 2** correct?

---

### Post by VMC on 2010-02-02
> **Merk42 said:**
> Um, which came out in October.

yasasflash, you're using **Lucid Lynx Alpha 2** correct?

If that becomes a yes, you could try re-installing Open Office. It works for me and I have Kubuntu 10.04 A2 installed.

---

### Post by jfernyhough on 2010-02-02
I imagine the repo hasn't had all received the OOo packages from the latest update (to 3.2.0rc4).

Either wait, try removing all OOo traces and reinstalling, or grab the debs from the OOo website. They actually work very well - I'm running them on both my Lucid and Karmic laptops.

[http://download.services.openoffice.org/files/extended/3.2.0rc4/](http://download.services.openoffice.org/files/extended/3.2.0rc4/)

You might try moving your ~/.openoffice.org folder so you get a fresh configuration. This also fixes some startup issues.

---

