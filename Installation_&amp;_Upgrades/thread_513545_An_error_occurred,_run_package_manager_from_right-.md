---
title: "An error occurred, run package manager from right-click menu"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by konungursvia on 2007-07-30
E: The package Opera needs to be reinstalled, but I can't find an archive for it.

Running sudo dpkg --configure -a did not work, as the thing can't find the original package.

I first tried installing the Feisty opera deb, (I have successfully upgraded with a clean install of Feisty), it didn't have permission to open itself, so I then installed the tar package, which only runs from the unpacked extracted directory, not from the menu. Now all package managers give this error and I can't seem to fix it manually.

---

### Post by konungursvia on 2007-07-30
Oh, and it was <type: systemError>

---

### Post by Pumalite on 2007-07-30
Can you run Synaptic?. I mean; does it run at all or it gets stuck somewhere?

---

### Post by konungursvia on 2007-07-30
I can run it, but it proposes removing filelight, and downgrading the kernel to the previous one, a -900 solution. Seems wrong, so I said no. EDIT: sorry, I meant aptitude, the one that proposes that solution.. Synaptic won't let itself really run, it opens and  gives that error message, then closes when I cancel or hit ok.

---

### Post by Pumalite on 2007-07-30
You can download a 'tar ball' of the incomplete package and install it yourself. That would solve the problem.

---

### Post by konungursvia on 2007-07-30
Thanks for your help. I tried that, but I'm not very good at tarballs, and unpacked it in my "peter" directory, one cd up from my desktop, and can't seem to properly install it, though I can run it from there, strangely. Should I move the unpacked directory somewhere else and try install again?

---

### Post by konungursvia on 2007-07-31
Yeah, I tried unpacking it and running install, which seems to work, but it's not in the directory or registry and the problem persists. I can run opera from where it unpacked, but the system seems to think it's not there, only the borked .deb of the same program from earlier. EDIT: I think i erred in using the package manager to unpack the tarball, so it didn't install properly. I guess I should have used the tar command in a terminal, but when I tried that, ./configure , make and make install didn't do anything, and I couldn't see a binary to execute.... confused.

---

### Post by konungursvia on 2007-07-31
One more thing: aptitude keeps telling me E: I wasn't able to find a file for the opera package. E. Couldn't lock list directory. Are you root?

Hope this sheds some light. This is frustrating.

---

### Post by konungursvia on 2007-07-31
Got a partial solution:

sudo dpkg --remove --force-remove-reinstreq opera

This cleared it up, mostly, except opera is stil listed, without an icon, in the Internet Applications menu. At least I can run package managers again.

---

