---
title: "Blank screen after selecting operating system in Grub"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Iskaros on 2010-05-10
I upgraded from 9.01 to 9.10 then to 10.04. When I select ubuntu from the grub bootloader screen, the screen goes black except for a small repeating line. It waits here for about 20-30 seconds as it starts up. It then breifly shows the splash screen for about 2 seconds then goes to log in as normal. Is there a way to make the splash screen into the start-up screen as it should?

---

### Post by eltonw on 2010-05-10
> **Iskaros said:**
> I upgraded from 9.01 to 9.10 then to 10.04. When I select ubuntu from the grub bootloader screen, the screen goes black except for a small repeating line. It waits here for about 20-30 seconds as it starts up. It then breifly shows the splash screen for about 2 seconds then goes to log in as normal. Is there a way to make the splash screen into the start-up screen as it should?
This is the new login screen and _the flashing dots are normal_. **Not a problem**. This is just an 'enhancement' in LUCID LYNX.

---

### Post by Iskaros on 2010-05-10
I have a semi-old acer, with broadcom, so to have ubuntu come with the right wireless drivers i had to backtrack to 9.04. However I noticed that when I started with wubi 10.04 (albeit without internet) there was no flashing line, and the splash screen loaded the way it should. However when I uninstalled it and reinstalled 9.04 (full non-wubi version) and upgraded it, the splash screen does not load it just appears and is replaced with the login screen and the blank flashing line is the for all intents and purposes the splash screen.

---

### Post by bumanie on 2010-05-10
My laptop computer does the same as you describe. If it is a real issue for you, you should consider putting in a bug report to launchpad and let the developers have a look. It would be a good idea to install bootchart and send the output as an attachment. Personally I,m not too fussed as long as it boots in reasonable time, unlike my 64bit desktop that hangs for 27 seconds after login.

---

