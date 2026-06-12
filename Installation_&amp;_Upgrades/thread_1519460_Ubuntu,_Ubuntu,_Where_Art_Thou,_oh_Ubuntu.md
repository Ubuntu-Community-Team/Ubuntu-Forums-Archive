---
title: "Ubuntu, Ubuntu, Where Art Thou, oh Ubuntu?"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by snerk on 2010-06-28
I just installed UBuntu 10.04 64 bit (dual booting with Windows 7, 64 bit).


My primary problems are:

============== BEGIN PROBLEMS =====================

1) The ONLY icon visible on the desktop is "WD Smartware".

Using it, I can browse my drives (except for an extended FAT drive, which seems unrecognized).


2) I sought a means of accessing a CLI (many years ago, I was a Unix developer - primarily in C, of course - and wanted to "go" where I would be more comfortable - a CLI).

Finding no CLI access, I googled it (under Windows), and read that it was in a chain beginning with "Applications" (e.g., Applications->Foo->CLI).

However, I see no icon labeled "Applications". I've brought up both high level context menus available (the menu for "WD SmartWare", and the menu for the desktop background, and see no "Applications" menu option).

3) I see no means of browsing the internet. Wait, I found an html file. If I double click it, the Firefox application opens.

I can the enter the URL I desire. However, I've found no means of starting Firefox other than double clicking an app-associated file.

4) I see no means of shutting the system down (other than a hard shutdown with on/off switch or pulling the cord).

5) A dialog, something like the following, keeps popping up :


---------- Grant access to 00001124-0000-1000-8000-00805F9B34FB ---------

Device 'Microsoft Wireless Entertainment Keyboard 8000' wants access
to service 00001124-0000-1000-8000-00805F9B34FB.

<Checkbox="Always grant access">   <button="Reject">    <button="Grant">
------------------------------------------------------------------------------------

I check the "always grant" checkbox, and click the "Grant" button.

The dialog box disapppears, but as As far as I can tell, it has no other effect.

Eventually, the dialog pops up again.

*** This behavior MAY have stopped. I'll investigate.


6) My wireless keyboard sometimes does not work with Ubuntu - it works fine in Windows.


Well, for some time it did not work. Pressing keys had no apparent effect.

Now it seems to work.

I'll try to gather observations and be more specific - regarding the diccumstances under which it does and does not work.


All I can say for certain is that following bootup, it will either work all the time, or not work at all.



7) I cannot use my Microsoft wireless keyboard in GRUB to select the boot OS (Windows vs Ubuntu).

I appears that my BIOS does not recognize the microsoft wireless keyboard.

On the other hand, I CAN use my Logitech Di Novo Mini to select the boot OS.


Incidentally, so far I have only been able to enter SETUP (bios level), and/or use adjust SETUP configuration on my computer using a corded keyboard.

I had thought I did it once with the Microsoft cordless keyboard, but I was probably mistaken.

================= END PROBLEMS ====================


Any help would be appreciated.


------------------------------------------------------

A: Because it messes up the natural order of the text.
Q: Why is it annoying?
A: Top-posting.
Q: What is the most annoying characteristic in a forum post?

---

### Post by nothingspecial on 2010-06-28
Sounds like you need your panel.

I think the default keybinding for launching a terminal is Ctrl Alt T

It might be Ctrl Shift T

Once you have one open try typing ```
gnome-panel &
```

---

