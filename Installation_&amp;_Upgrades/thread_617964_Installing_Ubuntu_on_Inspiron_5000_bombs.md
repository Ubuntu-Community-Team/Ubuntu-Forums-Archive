---
title: "Installing Ubuntu on Inspiron 5000 bombs"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by svetlo56 on 2007-11-19
I cannot install 7.10 on my Dell Inspiron 5000 computer. At the beginning, I get a bunch of "[Package] has zero elements" messages, and then installation continues until I get "Saving VESA state" after which it hangs (freezes) and the only way to restart is to pull the plug. I checked the CD, memory is 512MB and processor 600MHz. What can I do? I tried Safe mode installation, but same thing happens.

---

### Post by computercolin on 2007-12-29
I had a similar problem to yours (though I have an Averatec c3500 laptop) and I think my solution will suffice.

You need to get the alternate install disc, it uses a text interface that will work by default. Download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) but be sure to check the box "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

Then follow the steps to setup your system but DON'T REBOOT (if you do, its not the end of the world, but its a simple fix to do before reboot)

Don't let the installer restart, it will return you to the installer main menu. Choose to start a shell and then choose to start a shell on [/dev/sda1 or /dev/hda1 or whatever your drive comes out to be]

At the shell:
```
nano /etc/default/acpi-support
```

change "SAVE_VBE_STATE=true" to "SAVE_VBE_STATE=false"

exit and save (CTRL+X then yes then ENTER)

type exit in your shell and if you are returned to the menu, choose to reboot

If it doesn't work:
[INDENT]I had an issue with the shell. When I tried to edit the acpi-support file with nano, I got some kind of b-something error. If this happens:

switch to a different Virtual Console (CTRL+ALT+F2)

activate the console (yay busybox!) and do ```
nano /target/etc/default/acpi-support
```

edit the file the same ("SAVE_VBE_STATE=true" to "SAVE_VBE_STATE=false") exit (see above) and type exit at the console

return to the original VC (Virtual Console) (CTRL+F1) and type exit

if you're dumped into the installer menu, choose to reboot[/INDENT]


That should do it. I have to admit, some of that is paraphrased, I don't remember exactly what the installer says. Post back whether it works or not!

Colin

---

### Post by TygerTung on 2008-03-06
I also have a inspiron 5000 and it installed fine using the alternitive CD. It said somthing about acpi having a zero element package as well but it appears to have no effect.

I am unsure of what a acpi is anyway, is it very important?

---

