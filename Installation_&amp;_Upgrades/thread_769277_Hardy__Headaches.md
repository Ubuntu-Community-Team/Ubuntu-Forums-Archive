---
title: "Hardy  Headaches"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Scotsgait on 2008-04-26
Could anyone help me through what I need to do to sort out a couple of issues I'm having since upgrading my Kubuntu 7:10 to Hardy Heron ?

The first problem I came across was that Adept is no longer launching. Someone on the IRC Channel directed me to a historical issue which requires me to change a setting in /etc/hosts

The advice was helpful but .... I can't get save file once amended because I don't have the rights. In fact, it appears that I can't get into administrator mode anywhere (or, at least, in the applications I've tried). I think it may well be connected with other problem.

Any guidance (the simpler the better) would be appreciated.

Many thanks

Scotsgait

---

### Post by dstew on 2008-04-26
> I can't get save file once amended because I don't have the rights.I assume you tried sudo. Can you post the command that is not working, and the error message you are getting?

---

### Post by Scotsgait on 2008-04-26
> **dstew said:**
> I assume you tried sudo. Can you post the command that is not working, and the error message you are getting?

My  etc/hosts file reads:

127.0.0.1 localhost
127.0.1.1 dad-desktop.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I was told that the second line is wrong and should read

127.0.1.1 dad-desktop


If I edit the file and try to save it, I get a warning

[I]The document could not be saved, as it was not possible to write to file:///etc/hosts.
Check that you have write access to this file or that enough disk space is available.[/I]

I can't run any program using kdesu for some reason. I've also tried using Terminal and got an error *unable to resolve host dad-desktop*

---

### Post by dstew on 2008-04-27
Post the output of```
ls -l /etc | grep host
```

---

### Post by IT-Joker on 2008-04-27
> **Scotsgait said:**
> I was told that the second line is wrong and should read

127.0.1.1 dad-desktop

If I edit the file and try to save it, I get a warning
Yes, I had the same problem.
The thing is that you can't edit the file with normal privileges. So you need to escalate your privileges (sudo) to be able to save the file.
And now the point: sudo doesn't work because you have that line missing in /etc/hosts while you can't edit the file from your account because sudo doesn't work.

What you can do:
Reboot to recovery mode. It should put you to the command line. Then use:
nano /etc/hosts
to open that file in a simple text editor. There you should be able to add the line you mentioned to the file:
127.0.1.1 dad-desktop
save, reboot, it should work.

---

### Post by dstew on 2008-04-27
> And now the point: sudo doesn't work because you have that line missing in /etc/hosts while you can't edit the file from your account because sudo doesn't work.That's a great puzzle you solved. Thanks for explaining it. I was really perplexed by the OP's problem. Sorry I can't help you much with your own problem.

---

### Post by Scotsgait on 2008-04-27
Thanks, folk.  

I got it sussed late last night from the help I got[ here](http://kubuntuforums.net/forums/index.php?topic=3093748.0)

It's basically the same solution but uses *vi* instead of* nano*

Thanks again for your interest.

---

