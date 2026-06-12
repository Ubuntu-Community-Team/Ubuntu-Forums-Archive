---
title: "How to upgrade to  9.10??"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kuldeepsidhu on 2009-07-25
i am running ubuntu 9.04..how can i upgrade to this the alpha version of ubuntu 9.10..plz tell me the whole procedure..

---

### Post by Nburnes on 2009-07-25
```
sudo update-manager -d

```Then select the 9.10 button.

I wouldn't recommend it if you don't know what you are doing?

---

### Post by XDevHald on 2009-09-02
Nah, it shouldn't be that bad IF you do not know what you're doing. I am currently upgrade as we speak to the 9.10 and will post updates of how it's working. I was running 8.04 and went o 9.04 (upgrading) which took over 2 hours, not bad for DSL.

---

### Post by Netich on 2009-09-02
I usually wait until the beta comes out. I use VirtualBox until then.

---

### Post by taavikko on 2009-09-02
> **Nburnes said:**
> ```
sudo update-manager -d

```Then select the 9.10 button.

I wouldn't recommend it if you don't know what you are doing?

There's no need to use sudo on that one, update-manager is tied up to policykit and will ask for authentication if needed.

But I agree on the second part. If in doubt or similar, wait for the beta or rc, before upgrading. There are several bugs which can prevent usage.

---

### Post by GeorgeVita on 2009-09-02
Hi **kuldeepsidhu**,

just an additional note to previous:

from my small experience, update/upgrade within alpha version could be 'large' enough! For example from yesterdays daily build, today I had to download 180-200 MBytes more! As development is running many things are always changing...

Regards,
George

---

### Post by zoomy942 on 2009-09-02
just please be patient and remember this is a test build - it's gonna break ;)

---

### Post by ranch hand on 2009-09-03
> **zoomy942 said:**
> just please be patient and remember this is a test build - it's gonna break ;)
And while this breakage is FUN on a test drive or test box I don't think it would, in the least, be amusing if you need the box to WORK under the OS.

---

### Post by XDevHald on 2009-09-03
After pulling the box out of the closet with Karmic it is very slow and buggy, but not as bad as I expected it to be. Of course by default the drop down main menus don't have the icons for the gnome-panel and UbuntuOne does not work at all (Connect) is non-responsive.

Secondly, after upgrading from 8.04 to 8.10 the drag and drop and firefox handle was HORRIBLE and was reported to launchpad. I am running a fresh HDD on my AMD with Ubuntu 8.04 and won't be upgrading to Karmic but simply getting the CD instead when it's out of beta (atleast 3 months after.)

---

### Post by ChrT on 2009-09-03
> **Steven Myers said:**
> After pulling the box out of the closet with Karmic it is very slow and buggy, but not as bad as I expected it to be. Of course by default the drop down main menus don't have the icons for the gnome-panel and UbuntuOne does not work at all (Connect) is non-responsive.

Secondly, after upgrading from 8.04 to 8.10 the drag and drop and firefox handle was HORRIBLE and was reported to launchpad. I am running a fresh HDD on my AMD with Ubuntu 8.04 and won't be upgrading to Karmic but simply getting the CD instead when it's out of beta (atleast 3 months after.)

Yeah, someone forgot to read the giant bolded disclaimer on top of this forum section.

> **Ubuntu Karmic Koala is in development, use only for testing purposes!!!**

On the other hand, if you're looking for a more recent but stable version of Ubuntu, try 9.04 as opposed to the 8.04 LTS.

---

### Post by XDevHald on 2009-09-03
Nah I didn't forget to read this. I enjoy beta developments and have been for 4 years now with Ubuntu, but this was a little to heavy for my taste. I do have the 8.04 which is extremely stable and working great but not sure if I want to upgrade to 8.10 as the drag and drop+unstable firefox load (images and other) do not comply correctly.

---

### Post by dbc254 on 2009-10-24
Currently running 9.04 Kubuntu. Downloaded the Kubuntu 64bit version of 9.10 onto a CD. Is there a way to upgrade using this? I'm on dialup [downloaded iso at work] and would like to NOT tie up my phoneline downloading 200+mb.

P.S. Still clicking past the whitebox error on bootup "unable to find Xserver ---" using default.  I click "OK" and it finishes loading. Nobody's been able to figure out what the heezy's causin that error yet.

---

### Post by ranch hand on 2009-10-24
A little information on how you are installed now would be a big help.

---

