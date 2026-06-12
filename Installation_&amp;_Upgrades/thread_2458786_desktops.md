---
title: "desktops"
date: 2021-03-03
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2021-03-03
Lubuntu 20.04 has 4 desktops. i'm happy with only one. i've tried to find a way to limit to only one., my search terms aint working. can this be done?

---

### Post by guiverc on 2021-03-03
Four desktops?

What do you mean by four desktops?   I can only think of one (LXQt).

I booted a recent (*yesterday I think*) Lubuntu *hirsute* QA-test install, and it's options were

- **Lubuntu** (ie. the LXQt desktop with all Lubuntu scripts running; our intended experience)
- **LXQt Desktop**  (the same LXQt desktop, but without many Lubuntu scripts; so a purer upstream experience, but not all Lubuntu documented functions mentioned in the manual will work here)
- **Openbox** - no desktop is running, you're just using the window manager directly

LXQt (like LXDE before it) isn't tied to any WM, and Lubuntu uses Openbox; however Openbox is not a desktop and rather than restrict users from using it if they so choose, the option is there.

Either way, I see only a single desktop - LXQt.

(I used *hirsute* because it was handy, and being a QA-test install, it's stock without any changes made to it.  I also booted a *focal* daily and see the same three options in `sddm`).

It might help if you explain what you mean.

---

### Post by deadflowr on 2021-03-04
Do you mean workspaces?

---

### Post by guiverc on 2021-03-04
I'm now somewhat *redfaced* as I think @deadflowr has it in one.

Workspaces or changes to the number of *virtual* desktops can be made in openbox settings (it'll show as *Window Manager Preferences* on the screen)

Covered in the manual on page 

[https://manual.lubuntu.me/stable/3/3.2/3.2.11/openbox_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.11/openbox_settings.html)

---

### Post by GhX6GZMB on 2021-03-04
OP indeed used the correct terminology according to the LXQt Openbox settings.

---

### Post by oneleded on 2021-03-05
well; if ya can be of some help, that would be appreciated. besides, i dont need 4 work spaces at the moment, ;~} much less 4 desktops.
hard enough to keep track as it is. thanks
PS, i havent read the manual all the way through yet. to much else going on.

---

### Post by Rex Bouwense on 2021-03-05
Go to main menu->Preferences->LXQT settings->Openbox settings->desktops.  Once there merely change the Number of Desktops to the desired number and close.  (The default number is 4.  Change it to 1.)

---

### Post by TheFu on 2021-03-05
Run **obconf**. See the "Desktop" tab.  Tweak as desired.

---

### Post by oneleded on 2021-03-07
> **Rex Bouwense said:**
> Go to main menu->Preferences->LXQT settings->Openbox settings->desktops.  Once there merely change the Number of Desktops to the desired number and close.  (The default number is 4.  Change it to 1.)
that seemed to have worked. thanks more than ya know.
P.S. i also got rid of desktop switcher, right after.. Ha Ha

---

### Post by oneleded on 2021-03-14
if i need to come back, i will.

---

