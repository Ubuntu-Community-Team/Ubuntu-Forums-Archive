---
title: "How to alter the BIOS to allow boot from CD"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by humbll on 2007-02-24
**[SIZE="3"]How to set up the computer to allow you to boot from a cd-rom:[/SIZE]**

Step 1: Figure out how to get into the BIOS (aka COMS) Most computers will display a bit of text onscreen briefly when first booting up. It will say something like "Press DEL to enter setup" or "F2 To enter setup" or something of the sort. If your computer does not show this (look carefully) then you can experiment with different buttons by turning on the computer and then pressing each button in turn repeatedly whilst it bootstraps. If it begins to boot the Operating System (Starting Windows or whatever) just power down and try again with a different key. Begin hitting one key very fast from the moment you press the power button and don't stop until you see it begin to load the operating system. Then power down and move to the next key. Commonly used keys are:

F1
F2
F10
Insert
Delete - most Award and AMI BIOS will use this.

Acer - Ctrl+Alt+Esc
Compaq - F10
Compaq Presario - Press <Alt> <Ctrl> <Esc> at boot when you see the "Compaq" log in big letters
Dell - F1, F2 or Del.
Gateway 2000 - F1 or F2
Hewlett Packard - F1
IBM:
Older Models -  hold down both mouse buttons during boot-up.
Aptiva - Press F1
Fortiva 5000 - <Cntrl> <Alt> <A> or <Cntrl> <Alt> <S>
NEC - F2
Packard Bell - F1 or F2
Sharp Laptop 9020 - F2
Sony - F3, then F2, or F1
Tandon computers - Hold down the <Esc> key
Toshiba Laptops - Toshiba Utility, you can hold the ESC key during boot which will then prompt you to press the F1 key to enter the BIOS.

If none of these work for you then try all of the "F" buttons in order one at a time (F1, F2, F3, etc.)
and combinations like Ctrl-Esc, Alt-Esc, Ctrl-Alt-Esc, Ctrl-Alt-Enter

If you still cannot get in I advise you to contact the computer manufacturer to see how it is done.

Once you are in look for Boot Options navigate to it, and set it to boot from the CD first. Then save and exit the bios. (You will see instructions for navigating around the BIOS and saving etc once you are in there. Usually you will navigate by using the up and down arrow keys to highlight the Boot Options section then press enter.  They are all different so just look at the top or bottom for instructions specific to your machine once you are in there. Once done save, exit , reboot and it should load the CD, if not, try rebooting a few times both with ctrl-alt-del and with the reset or power button. If still no luck re-enter BIOS and verify settings are correct. If so, the CD may be defective or the Drive may be, or maybe you did not [burn the disk as an ISO image]("https://help.ubuntu.com/community/BurningIsoHowto")?

---

