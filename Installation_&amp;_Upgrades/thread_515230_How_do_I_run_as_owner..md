---
title: "How do I run as owner."
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2007-08-01
Well I need to write to my _user\bin\_. but it is not wont let me. So I tried to change the accsess properties and it says I am not runing as owner.

---

### Post by dfreer on 2007-08-01
I think the simplest answer, although I don't know what you are trying to accomplish here, would be to try this command:
```
sudo nautilus /usr/bin/
```
and then enter your password. Be careful when mucking about the filesystem as root!

---

### Post by Pumalite on 2007-08-01
Try: sudo chmod 777 /usr/bin

When you are done: sudo chmod 000 /usr/bin

---

### Post by Jeremywilms on 2007-08-01
lol. I need to accsess it to install a windows emulatore

---

### Post by dfreer on 2007-08-01
> **Jeremywilms said:**
> lol. I need to accsess it to install a windows emulatore

Can you be more specific on what the program is? Any guide's, how-to's or instructions you may be following to get it installed?

---

### Post by Jeremywilms on 2007-08-01
Hmm I feel like an idiot now but what I ment to say was I need accsess to _usr\local\bin_
Though I tried the same command with it and got
> bash: /usr/bin/sudo: Permission denied

---

### Post by dfreer on 2007-08-01
The command to open nautilus as root within the /usr/local/bin/ directory should be:
```
sudo nautilus /usr/local/bin/
```

---

### Post by olieviya on 2007-08-01
The best thing to do when installing a windows emulator, like wine is to follow a how-to/tutorial/wtv. Also since you are a newbie it would not be so wise to go "messing around" as root in folders, maybe you could even do it automatically with Synaptic, which can be found in System>Administration/Synaptic Package Manager, which makes everything easier than doing it manually.:)

---

### Post by dfreer on 2007-08-02
Once again, specifics on what you are trying to do and what program you are trying to install would make it eaiser for us to give you good advice ;)

---

### Post by D4mn on 2007-08-02
> **Pumalite said:**
> Try: sudo chmod 777 /usr/bin

When you are done: sudo chmod 000 /usr/bin

? setting your /usr/bin rights to 000 afterwards does not really seem a good idea to me. Better check what the rights are on the dir and put them back exactly the way they were.

---

### Post by monogan on 2008-07-05
I made a bad mistake here. I said "sudo chmod 000 /usr/" Now my computer won't start-up. Is there anything I can do?

---

### Post by Victormd on 2008-07-05
Have you tried starting in safemode?
What about CTRL+ALT+F1?

---

### Post by monogan on 2008-07-05
> **Victormd said:**
> Have you tried starting in safemode?

How do I do that? It doesn't even bring-up the login script. It just shows a gobbedy-goo box and a button I can click. Then it tries to restart and does the same thing. Would F2 at the start or something like that get me into safe mode?

---

### Post by arashiko28 on 2008-07-05
according to what I've read > you just remove the abilities to do anything w/ the files or folder of what you just chmod to 000, but you can still change it back to whatever you prefer. i.e. chmod 700
[http://www.unix.com/unix-dummies-questions-answers/9543-chmod-000-a.html](http://www.unix.com/unix-dummies-questions-answers/9543-chmod-000-a.html)

go on recovery mode, that is press escape before the GRUB countdown ends and choose there run as root them do what you did before changing the numbers, i'm not pretty sure if it'll work, but at this point you have nothing to loose.

Good luck

---

### Post by monogan on 2008-07-05
OK, I see now how to get into safe mode. Now here's my problem. I enter "chmod 777 /usr/" and it says "Operation not permitted" Any ideas? Thank you all for your help so far. I'm certainly a little panicked.

---

### Post by monogan on 2008-07-05
OK, here's the catch-22 I seem to be in when I log into safe mode. I can't say "chmod 700 /usr/" because I need to convey that I am root. When I try "sudo" it doesn't recognize the command because that's within "/usr". I tried to set myself as root with "su", but it says "Authentication failure".  Any other ways I can gain root access?

---

### Post by steveneddy on 2008-07-05
When you get your 'puter booted, please tell us what application you are trying to install and stop mucking around in the /bin files.

The application will install itself where it needs to go.

Please tell us the name of the "program" you would like to install before you hose the system.

Some of the advise you are getting will make you system unbootable, as you can see. Going into the /bin files should be done with caution. Unless you know what you are doing, please ask us how to install a particular piece of software. I'm sure we've seen it before and you won't be telling or asking anything that we haven't seen or done before.

---

### Post by monogan on 2008-07-05
Oh yes, lesson learned. I won't be mucking around in that any more. The good news is that I finally saved my computer. The advice that worked was as arashiko28 said, to do recovery mode in "root". This did in fact let me reverse the file permissions. Thank you all, and on behalf of all n00bs, we'll be taking your advice, steveneddy.

---

