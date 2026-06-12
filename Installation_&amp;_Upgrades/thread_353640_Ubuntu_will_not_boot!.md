---
title: "Ubuntu will not boot!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Rabbit_Alex on 2007-02-04
I installed Ubuntu 6.10 today, and it was working until I turned it off later.

Now when I start the computer, the GRUB loads up and I select Ubuntu, and the Ubuntu progress bar runs for a minute.

The problem is that after the progress bar, Ubuntu stops loading and a cursor just stays on the screen and it doesn't move past that.

What can I do?

---

### Post by Rabbit_Alex on 2007-02-05
I'm bumping this thread up so hopefully someone can answer my question.

Thanks ):P

---

### Post by Dylnuge on 2007-02-05
If you wait a while, does the cursor eventually show an error that mentions your hard drive (hard drive is usually /dev/hr0 or sr0, may be mentioned as device hr0 or sr0). I am having this problem as well and am running diagnostics on it currently.

Sincerely,
Dylan Nugent
Director of Product Development
Tranzerk Technologies
[email]dnugent@tranzerk.com[/email]

---

### Post by kebes on 2007-02-05
When you're at the stage where the computer is seemingly frozen, try using Ctrl+Alt+F1 (go through the F-keys from 1 to 12) to get to the background consoles. (You may have to use Alt+Fn instead, depending on what stage of the boot you're at.)

The point in going through these background consoles is to:
(1) Determine if the computer is totally frozen or merely stalled. (If you can't even flip through those sessions then the computer is really frozen!)

(2) In all those screens, look for any error messages the kernel might be out-putting. If you see activity in one of those screens, look at what is going on. If there are any errors, copy them down and post them here. They will help in understanding the problem.


Also, can you be more specific about what stage of the bootup it freezes at? When you say "cursor" do you mean a cursor on the commandline, or do you mean the mouse pointer? Is this as the graphical environment (gnome) begins loading (you see a brown screen with a white mouse pointer) or is this before that (a dark background with just "Ubuntu" and a progress bar...).

---

### Post by Rabbit_Alex on 2007-02-05
What I mean by cursor is the command line.  The screen is completely black except for the cursor.

It is the screen in between the Ubuntu progress bar and when Gnome starts loading.

I will now try the Ctrl+Alt+F1.  Back in a few minutes.

---

### Post by Rabbit_Alex on 2007-02-10
I reinstalled using the alternate CD, so everything is fine.

---

