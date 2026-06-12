---
title: "upgraded to 20.04.1 LTS, ttf-mscorefonts-installer issues"
date: 2021-01-09
forum: Installation &amp; Upgrades
---

### Post by geovasiliu on 2021-01-09
hi, i just upgraded from 18 to 20 and after install there is a pop-up asking me to run ttf-mscorefonts-installer. it then attempts to send me to auth as admin but that window closes in a half a second. every time i try it does the same thing.
i opened LIbre Office and it seems allright... is ttf mscorefonts required only if i open ms word into Libre, or is it critical? thanks!

(also during installation there was a weird eula agreement window, without any ok, or accept buttons, only help, back and next buttons and for a while it looked like i will have to abort, then later by itself, it resumed the installation)

---

### Post by ajgreeny on 2021-01-09
> **geovasiliu said:**
> hi, i just upgraded from 18 to 20 and after install there is a pop-up asking me to run ttf-mscorefonts-installer. it then attempts to send me to auth as admin but that window closes in a half a second. every time i try it does the same thing.
i opened LIbre Office and it seems allright... is ttf mscorefonts required only if i open ms word into Libre, or is it critical? thanks!

(also during installation there was a weird eula agreement window, without any ok, or accept buttons, only help, back and next buttons and for a while it looked like i will have to abort, then later by itself, it resumed the installation)
I am not sure if it's necessary to have the  ttf-mscorefonts installed though I admit that I do have them and it seems to be used only if I open a doc from a Windows user who has used one of that font family.
If you don't have, for example, Times-New-Roman or Arial available I think LO will use the Liberation family equivalent and they seem to work fine.

I suspect the weird EULA window that you saw simply needed you to press Tab to highlight the OK (or is it Accept) button; many users find it difficult to know what to do there and just give up, as you did.  Try again.

---

### Post by Impavidus on 2021-01-09
The ttf-mscorefonts-installer package is required if you want to use MS core fonts or Wine, as the Windows applications running in Wine are guaranteed that those fonts are available. I don't have those MS fonts on my computer.

---

### Post by ajgreeny on 2021-01-09
Useful info, thanks Impavidus.

I haven't used Wine for many years and was not aware of that need for the mscorefonts; it doesn't appear to be a dependency nor a recommended package of wine so perhaps it is just more helpful if it's installed.

---

### Post by CatKiller on 2021-01-09
You don't need them for Wine. They'll be used if they're there, but other fonts with the same metrics exist and will be used otherwise. They were created for websites to use, but you don't need them there, either, since the "how do we ensure the reader has the font we're using on our page" problem was solved differently a long time ago. And they aren't very good fonts; they lack coverage and the hinting relies on Windows' prior "snap everything to pixels" behaviour.

So install the package if you really really need Arial and Times New Roman with no substitutions, or don't if you don't.

---

### Post by T6&amp;sfpER35% on 2021-01-09
[https://itsfoss.com/install-microsoft-fonts-ubuntu/](https://itsfoss.com/install-microsoft-fonts-ubuntu/)

---

### Post by Impavidus on 2021-01-10
> **ajgreeny said:**
> Useful info, thanks Impavidus.

I haven't used Wine for many years and was not aware of that need for the mscorefonts; it doesn't appear to be a dependency nor a recommended package of wine so perhaps it is just more helpful if it's installed.

I've never used Wine myself, this was something I picked up on this forum. But maybe it's no longer true; I haven't checked.

Edit: Just checked it. ttf-mscorefonts-installer is suggested by playonlinux.

---

### Post by kurt18947 on 2021-01-10
Does having MS fonts installed help with the .docx -> .odt -> . docx editing? I find it easy enough to install MS fonts and feel like doing so provides one less thing to go wrong when interacting with MS office users.

---

### Post by CatKiller on 2021-01-10
> **kurt18947 said:**
> Does having MS fonts installed help with the .docx -> .odt -> . docx editing? I find it easy enough to install MS fonts and feel like doing so provides one less thing to go wrong when interacting with MS office users.

Kind of, but not really. Those fonts are *old*, and not the defaults in Windows any more as far as I'm aware. *If* someone's sent you a document that uses those specific old fonts, then your having those fonts saves a conversion to a different one, and then another potential conversion when you send them back. If they're using a different font, though, like one of the newer Windows fonts, then having some old Windows fonts installed on your system is no help at all.

---

