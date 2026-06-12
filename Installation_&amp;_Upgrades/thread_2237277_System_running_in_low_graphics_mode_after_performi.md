---
title: "System running in low graphics mode after performing recent hardware update"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by lennybogart on 2014-07-31
Right, so the update manager on my 12.04 Ubuntu machine asked me to perform a hardware update. I did so but now the thing won't boot past a screen that tells me 
"The system is running in low graphics mode
Your screen, graphics card, and input device settings could not be detected correctly.
You will need to configure these yourself."

When I click ok, it takes me to a list of 4 other options including -

Run in low graphics mode just for one session
Reconfigure graphics
Troubleshoot the error
Exit to console login

The 4 options above are as useless as each other meaning none of them allow me to.do anything except look at the boot error log.

I am so upset by this. I in no way expected something like this to happen thanks to good 'Ol Canonical!!

What the hell do I do?

Someone please help me...

---

### Post by papibe on 2014-07-31
Hi lennybogart. Welcome to the forum ):P

Could you open a terminal, run these commands and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'

ls /etc/X11/xorg.conf

```
Regards.

---

### Post by lennybogart on 2014-07-31
How should i open the terminal? It won't even let me do that, I don't think :(

---

### Post by papibe on 2014-07-31
Try pressing:
```
Ctrl+Alt+t
```
Regards.

---

### Post by lennybogart on 2014-08-01
Doesn't work!! :( :( :(

---

### Post by kansasnoob on 2014-08-01
Try Ctrl+Alt+F1 to open a terminal.

We should at the very least know what graphics chip you have. You can see by running:

```
lspci | grep VGA
```

BTW that's a lower case L at the beginning.

While you're in the terminal it might be worthwhile to run:

```
sudo apt-get update
```

Then:

```
sudo apt-get -f install
```

The latter of the two may give you some hints regarding missing dependencies or such.

It's also possible that you could apply the ***nomodeset*** boot parameter prior to booting:

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Have you ever done something like that before?

If not jump down to **Temporarily Add a Kernel Boot Parameter for Testing** on that page. Is that understandable?

I ran into a similar problem:

[http://ubuntuforums.org/showthread.php?t=2236584&p=13084647#post13084647](http://ubuntuforums.org/showthread.php?t=2236584&p=13084647#post13084647)

But I was able to boot to the desktop - just a horrible looking one - so I could muck about using the UI. I'm not very good at X issues :(

Maybe that little bit of info can help someone else more knowledgeable regarding X to help you.

---

### Post by lennybogart on 2014-08-02
It's okay people. I have managed to reinstall Ubuntu after about 6 attempts.

I had to try various different configurations. The one that worked was - without asking for password before log in and no encryption of home folder.

If I tried to install with the home folder encrypted, at the password page after start up the drums would keep rolling, again and again, then it would crash/freeze. I have no idea what it was? I'm so glad there wasn't loads of important stuff on there!!

And no keyboard shortcuts would work. So all the people telling me to press <Ctrl> <Alt> <t> or <Ctrl> <Alt> <F1> or <F2>, it just didn't work?

Anyway, it all went wrong after I tried to update the computer. And I have a GE Force graphics card, not 100% sure which one though.

---

