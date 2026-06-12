---
title: "windows boot from disk error"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by help plz on 2010-05-22
I'm trying to install ubuntu from a disk I got with a Ubuntu manual magazine, but once I choose the install option, the logo glows for a couple minutes then freezes and nothing happens.

The same happens for running it without installation.

Does anyone know what I should do? I'm currently downloading it onto a USB stick to attempt to boot it from that.

Thanks in advance.

UPDATE: After browsing for solutions I tried using "noapic" and "nolapic" options but neither helped :(

---

### Post by darkod on 2010-05-22
When the cd starts loading and you see the splash image, hit any key to get a menu. Then hit F6 and select Safe Graphics.

After that, you should be able to select Try Ubuntu and that will try to load it with safe graphics. It might be video driver issue usually.

If you can boot in safe graphics, you could install, but at first boot you also need to log in this way (or similar if different menu options are shown). Once you have fully booted the installed ubuntu, it will probably find the correct driver and offer to install it.

---

### Post by help plz on 2010-05-22
okay thanks I'll give that a try.

UPDATE: Nope I get the same problem with safe graphics. Any other suggestions? :(

---

### Post by darkod on 2010-05-22
Another thing to try is:

Hit any key to get the menu. Highlight the Try Ubuntu entry but don't hit Enter. Hit 'e' instead.

That will show you the boot commands for editing. Use the arrows keys and End and go to the end of the line starting with linux.

When you are at the end of that line, use Backspace and delete quiet and splash, and write instead nomodeset

Then press Ctrl + X to try and boot. If it helps, we can make that parameter permanent.

---

### Post by help plz on 2010-05-22
okay I highlighted the try option but E did nothing, so I pressed f6 and closed the menu which opened, leaving the line of text open below. I replaced quiet & splash with nomodeset then ctrl + x did nothing so I hit enter.

That opened a load of white text which said it was setting up lots of stuff, then stopped on "setting preliminary keymap" I'll tell you if it changes from that, but it's been on it for a while

UPDATE: Nah, it's stuck on that. Turned it off now I'll give it another try tomorrow. Any more suggestions are welcome of course :P

---

