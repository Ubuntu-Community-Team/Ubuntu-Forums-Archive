---
title: "Upgrade from 9.10 to 10.04 fails"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by MadeTheSwitch on 2010-05-19
Argh! I've been using Ubuntu since Hardy; I have never had this issue before, even as I went from Hardy to Intrepid, Intrepid to Jaunty, and finally to Karma.

I tried searching for a solution here but no luck thus far in terms of finding an idea that solves the problem. Which is:

When I try to upgrade from Karmic to Lucid, I get the error in the attached screenshot. The error is:

--
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade. 
E: unable to correct problems, you have held broken packages. 
--

(the message then explains what could cause it but none of these apply; furthermore, I have disabled all outside sources, cleaned up apt-get, ran apt-get update, install -f, and dist-update, and it's still happening)

I am also attaching the main.log file from the dist-upgrade directory. It's in two separate files because of the size limit. 

Please HELP!

---

### Post by MadeTheSwitch on 2010-05-19
*beg* please?

---

### Post by Catharsis on 2010-05-19
It's generally considered poor forum etiquette to bump your thread less than 24 hours after the last post (just to be respectful of the other people who need help too :))

That said, please post your sources.list file with code tags around it
```
cat /etc/apt/sources.list
```

---

### Post by MadeTheSwitch on 2010-05-20
> **Catharsis said:**
> It's generally considered poor forum etiquette to bump your thread less than 24 hours after the last post (just to be respectful of the other people who need help too :))


I am so sorry, I didn't know that. I will not do so again in the future. 

Anyway, I solved my own problem.

What I did was go to Synaptics and look for all the "non-standard" packages - things installed by third parties, or things I installed outside the mainstream. I was particularly looking for xorg related stuff because the log file (which I attached above in my original message) seemed to suggest that was what was throwing off the update tool.

To cut a long story short, once I identified those packages (there were about 10 of them related to xorg), I went and downgraded them to the basic Ubuntu Karmic ones. 

Then I reran the update tool and lo and behold, it went through no problem. I am writing this post from a 10.04 laptop, which by the way, came back with pretty much most stuff intact; the only thing I need to figure out is how to make USB work again, and my NFS mounts no longer come up automagically. 

I do want to let others know though: if you run into this issue, you need to do three things:

1) uncheck all the entries under "other software" in Synaptics (so that the update doesn't try to update anything other than Karmic itself)
2) look into the main.log file under /var/log/dist-update/ - go to the most recent date and number combination in the directory names - and look at the bottom of it. It will tell you pretty explicitly which package is causing the issue (the last one before it throws the error and exits). 
3) look for that package and all its related things in Synaptics and use the package->force version action to downgrade them.

This should take care of the problem and allow the upgrade.

---

### Post by xtracool_protik on 2010-05-20
Hey thanks that worked well for me :D

---

