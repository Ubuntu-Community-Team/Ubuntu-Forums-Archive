---
title: "Restore ubuntu bootsplash"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by jncolin on 2006-07-06
Hi

I originally installed Ubuntu distro on my laptop, then, I added kubuntu-desktop package, that also changed by bootsplash screen. I could get rid of all the kde stuff, but I can't restore the bootsplash to the original one (the one that came with ubuntu).
I tried uninstalling/reinstalling ubuntu-desktop, without success.

Can someone help?

Cheers

Jean-Noel

---

### Post by rcarring on 2006-07-06
Remove usplash using the instructions on the wiki page about installing ubuntu on ms virtual pc (bear with me) as it should then allow you to add the uspash that you actually want, the msvpc is crap at running ubuntu and the page tells you how to remove usplash, the reason I mention it.

---

### Post by jncolin on 2006-07-06
Thanks a lot, this worked easily

---

### Post by hda on 2006-07-06
Use this command to choose from the available boot splash images:
```
sudo update-alternatives --config usplash-artwork.so
```
_hda_

---

### Post by palintheus on 2006-07-10
I ran into this thread looking for a solution to this problem after installing/removing the kubuntu-desktop using aptitude, but when I enter the command to choose the artwork it gives me this. I also tried to search for how to remove the usplash on the wiki, but cannot find it.

```

trey@desktop:~$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```


Help Please?

---

### Post by JoshHendo on 2006-07-11
I am having the same problem too.

I ran
```

sudo update-alternatives --config usplash-artwork.so

```

And when I shut the computer down, the usplash there was fine, but when I booted up, it still had kubuntu. So it is now ubuntu on shut down and kubuntu on bootup :p.

When I do that again, I get what palintheus gets. Is there a way that I could fix this? Thanks!

---

### Post by palintheus on 2006-07-11
This is something I forgot to mention -- The below happens to me too.

> **JoshHendo said:**
> And when I shut the computer down, the usplash there was fine, but when I booted up, it still had kubuntu. So it is now ubuntu on shut down and kubuntu on bootup :p.


It is really annoying ](*,)

---

### Post by JerryC on 2006-07-11
> **rcarring said:**
> Remove usplash using the instructions on the wiki page about installing ubuntu on ms virtual pc (bear with me) as it should then allow you to add the uspash that you actually want, the msvpc is crap at running ubuntu and the page tells you how to remove usplash, the reason I mention it.

I've never been on a wiki.  Could you educate me on how to find that page please?

JC

---

### Post by palintheus on 2006-07-11
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by JerryC on 2006-07-11
> **palintheus said:**
> [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Thanks, but I found that page.  While there are a lot of options there, none of them seem to be for any technical information.  In the meantime I solved the problem.  I found a "How-To" sticky note in these forums.

JC

---

### Post by palintheus on 2006-07-11
> **JerryC said:**
> In the meantime I solved the problem.  I found a "How-To" sticky note in these forums.

JC

Do you mind posting the link?

---

### Post by JerryC on 2006-07-11
> **palintheus said:**
> Do you mind posting the link?

[http://www.ubuntuforums.org/showthread.php?t=82835&highlight=bootsplash](http://www.ubuntuforums.org/showthread.php?t=82835&highlight=bootsplash)

I have never posted a link before.  I don't know if this will be clickable or not.

JC

---

### Post by mattkenn4545 on 2006-07-11
Might try the seach feature?

---

### Post by palintheus on 2006-07-11
> **mattkenn4545 said:**
> Might try the seach feature?

I did search, that is how I found this thread.


Thanks JerryC.

---

