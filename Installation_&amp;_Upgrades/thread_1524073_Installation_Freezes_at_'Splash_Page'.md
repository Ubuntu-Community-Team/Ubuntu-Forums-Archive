---
title: "Installation Freezes at 'Splash Page'"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by EinhanderSoul on 2010-07-04
I was attempting to install Xubuntu 10.04 the other day using a USB stick via the Universal USB Installer to make it bootable, I was able to access the install screen but when I try to hit either "Boot Ubuntu Live via USB" or "Install Ubuntu on Hard Drive" it takes me to the Xubuntu splash screen which took forever to load to a point where I think it froze... :-(

Am I doing something or is there a work around for this?

I'm still stuck with Windows...

---

### Post by davidmohammed on 2010-07-04
probably a graphics issue - the answer depends on what graphics card you have.

On the install screen where you choose the language and "try ubuntu without installing" etc - press F6.

at the bottom is a line of what looks like gibberish.

add one of the following options immediately before quiet splash --

nomodeset
i915.modeset=1
i915.modeset=0

then choose "Try ubuntu without installing" - do you get to the desktop?

---

### Post by EinhanderSoul on 2010-07-04
> **davidmohammed said:**
> probably a graphics issue - the answer depends on what graphics card you have.

On the install screen where you choose the language and "try ubuntu without installing" etc - press F6.

at the bottom is a line of what looks like gibberish.

add one of the following options immediately before quiet splash --

nomodeset
i915.modeset=1
i915.modeset=0

then choose "Try ubuntu without installing" - do you get to the desktop?

I have an old 64 MB Nvidia MX/MX 400, thanks I'll try this later again after School. :)

---

### Post by Will Shackleton on 2010-07-04
Have you tried the 'Alternate CD'? It is a command-line version of the installer. However, I think that you will need to get hold of a USB CD drive, or find out how to write the CD to a USB stick (google it).

You can get the Alternate CD at [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-alternate-i386.iso]("http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-alternate-i386.iso")

---

### Post by EinhanderSoul on 2010-07-05
> **davidmohammed said:**
> probably a graphics issue - the answer depends on what graphics card you have.

On the install screen where you choose the language and "try ubuntu without installing" etc - press F6.

at the bottom is a line of what looks like gibberish.

add one of the following options immediately before quiet splash --

nomodeset
i915.modeset=1
i915.modeset=0

then choose "Try ubuntu without installing" - do you get to the desktop?

No, let me rephrase it... It was the "Boot Menu" that I was on, not the Installation Menu...

I have these choices there:

1. Boot Xubuntu Live Via USB
2. Install Ubuntu on this Hard Drive
3. Test memory space
4. Help>
5. About

Now if I hit either the 1st and 2nd option it takes me to the Xubuntu Splash Screen that took forever to load, possibly stuck...

---

### Post by EinhanderSoul on 2010-07-05
I hate to do this but, "bump"

---

### Post by davidmohammed on 2010-07-05
look at the files via windows on your memory stick - you should have a "text.cfg" file - add the boot option there.

---

### Post by EinhanderSoul on 2010-07-06
> **davidmohammed said:**
> look at the files via windows on your memory stick - you should have a "text.cfg" file - add the boot option there.

I'll try this at a later time again, our Internet connection was cut off, I'm on a Net Cafe right now, but I'll post the results to what happened and thanks for the replies :p

---

