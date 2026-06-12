---
title: "Error messasge at startup?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by WoDan23 on 2008-05-11
right after selecting ubuntu in my dual-boot with xp HP it says "dmi_string: out of memory. and then "MP-BIOS bug: 8254 timer not connected to...something cant read the rest its too fast. then i could not log into Ubuntu normally, i had to do it under GNOME failsafe version. any ideas?

---

### Post by Rallg on 2008-05-11
I looked around via web search, and discovered that the error messages do not necessarily mean that there is a real problem. There are others who get similar error messages, but can boot. My own computer gets an error message of a different type, and it boots just fine. Others report the same thing.

So, although your eror messages MAY indicate a problem, it is also possible that they are not related to the problem that you do have.

If you can log in via Gnome failsafe, but not normally, it usually means that there is a hardware driver problem. Before you do anything else, disconnect anything unnecessary from your computer (iPod, external hard drive, scanner, whatever). Then attempt to boot normally. If you succeed, then the problem probably lies with drivers associated with your peripherals.

If you still cannot boot (except in failsafe) with minimal hardware, then some possibilities are your graphics card driver, wireless, maybe others. I suggest loggin in as failsafe (or in recovery mode), then in terminal:
sudo apt-get && sudo apt-get upgrade
and see if that brings in any new drivers. If so, reboot. If still no success, then come back here with a complete description of your system, and maybe others with similar hardware can help.

---

### Post by WoDan23 on 2008-05-11
ok thanks for the advice ill try that and get back to you. However, one thing i noticed a second ago was that when i tried to change the visual settings from none to a little it just restarted ubuntu, not the whole computer just the OS. I found that a little strange, but ill still try what you said.

---

### Post by WoDan23 on 2008-05-11
Ok now i got the visual effects working properly, but i still got the out of memory error.

---

### Post by Rallg on 2008-05-11
Is the "out of memory error" really an error, in that it stops the show? Or does it just say that, but keep going as if nothing happened?

What is your hardware? (Graphics card, memory, processor)?

From what you wrote, it sounds as if your computer uses a graphics configuration that was not properly initialized, or needs a different graphics driver. I'm not an expert in that sort of stuff, but you can't expect more help unless you reveal your hardware, so that others with the same stuff can compare.

Some graphics drivers do not allow fancy desktop effects. That's just the way it is.

---

### Post by WoDan23 on 2008-05-11
ok so now, Ubuntu just randomly restarts my computer from time to time, i have no idea whats going on. i wont even be sitting at the computer and it will just restart on me. i have no idea how to fix it. thinking maybe a new install?

---

