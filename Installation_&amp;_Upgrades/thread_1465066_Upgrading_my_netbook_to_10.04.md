---
title: "Upgrading my netbook to 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by 47of74 on 2010-04-29
I'll probably be taking my netbook up to Lucid here in a few days.  My question is if I should bother with the Netbook Edition or just get the standard edition?  Are there any packages in the netbook edition that can help with processing, power, etc on a netbook?  More importantly, can the special netbook desktop be turned off in favor of the standard UI?

---

### Post by Sprutnik on 2010-04-29
I think you should go for UNE. In 10.04, you have the option, at the login screen, to either login to UNE or standard Gnome.

---

### Post by 47of74 on 2010-04-29
> **Sprutnik said:**
> I think you should go for UNE. In 10.04, you have the option, at the login screen, to either login to UNE or standard Gnome.

Sounds like a plan - I think I'll do that once 10.04 becomes available for download.

---

### Post by moonport on 2010-04-29
> **Sprutnik said:**
> I think you should go for UNE. In 10.04, you have the option, at the login screen, to either login to UNE or standard Gnome.

I didn't know about it (both login's screen).
Thanks for the tip.

---

### Post by snowpine on 2010-04-29
If you like the "launcher" interface, install UNE. If you prefer the Gnome desktop, install "regular" Ubuntu. That's the only major difference.

---

### Post by Guy Sibley on 2010-04-29
Would there be a significant difference in functionality?

---

### Post by snowpine on 2010-04-29
> **Guy Sibley said:**
> Would there be a significant difference in functionality?

No; they share the same software repository and run the same applications. :)

---

### Post by ben1986 on 2010-04-29
No there's no difference in functionality, the UNE places a small demand on your graphics card, but thats about it.  I know this because my ancient X31 couldn't handle the Jaunty UNE, but upgrading to Lucid fixed everything.  I think the only difference was the size of the bootdisk (though I might be making that up) because I think I chose UNE because I was creating a Live SDHC card to install from, and the UNE was a smaller file.  But I could be wrong...


If your netbook is a real netbook, then the UNE is for you, but if the screen is big enough that the gnome environment would work I recommend going for that.

---

### Post by Gidskid on 2010-04-29
Is there an upgrade version? I've tried doing through the upgrade manager but it says it can't download the release notes? Any Ideas?

---

### Post by ben1986 on 2010-04-29
What do you mean by download notes?

Does upgrade manager not offer the 10.04 upgrade option?

if not, try alt+f2, then typing "update-manager -d" (without the quotes)

---

### Post by Gidskid on 2010-04-29
Update Manager gives me the option to upgrade, "-d" returns an error?

---

### Post by ben1986 on 2010-04-29
Ok, then what happens after you click on the upgrade button?

What do you mean by download notes?

I'm confused as to what exactly is the problem here :) I'm assuming you're running 9.10 at the moment, you open update manager, you see the option button for upgrading to 10.04, you're clicking it, and it is installing the packages and upgrading the system.  Is this the case?  I'm unsure as to what problem you need solving.

---

### Post by Gidskid on 2010-04-29
Ok well I open the Upgrade Manager, click upgrade to LTS and then it gives me an error. I tried it in the terminal also and this is what i Got:

update-manager -d

(update-manager:7519): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-GeI7SBt97Z,guid=1dd72cf960ef9ec44b633bf34bbed73c failed: Failed to connect to socket /tmp/dbus-GeI7SBt97Z: Connection refused.

---

### Post by ben1986 on 2010-04-29
Right, sorry mate, I'm not much use to you then, still pretty new myself.

I'm sure a more knowledgeable type will come in soon and reveal all :)

---

### Post by snowpine on 2010-04-29
> **Gidskid said:**
> Ok well I open the Upgrade Manager, click upgrade to LTS and then it gives me an error.

What exactly is the "error"? 

update-manager -d won't work any more because 10.04 is no longer the development release

---

### Post by zoomy942 on 2010-04-30
so i have the netbook edition now - but no desktop effects.  is this normal?

---

### Post by Gidskid on 2010-05-01
Fixed upgraded without any more problems, its not very different from 9.10, i'm not convinced it was worth it tbh

---

### Post by mihar on 2010-05-02
If you need more tips on optimising the new release on a netbook, check out my post on this: [http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04](http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04)

I mostly replaced the built-in netbook tweaks, for even more lightweight options :-)

---

### Post by lostcarpark on 2010-05-15
> **Gidskid said:**
> Fixed upgraded without any more problems, its not very different from 9.10, i'm not convinced it was worth it tbh

Boot up time seems a lot faster on my Asus Aspire One - reduced from over a minute to about 30 secs. That's worth it for me.

---

### Post by interglossa on 2010-05-15
I have UNE10.04 for my vintage ASUS EEE 701 which I still really like - but the startup time on the flash drive is still very slow (5 minutes) but with the caspar file system and the flash drive factored in I would like to think that is not so surprising.  Has anyone had a good experience running UNE 10.04 on a 701 (the first netbook sold and of course much more modest in cpu and ssd space as later models).

Also I notice that they have separate mount points under /var which eats up half a gig which is not great, plus I prefer the earth tone themes of the early ubuntu to this purple haze background.  They had perfection and really didn't need to change it.  But I am mostly concerned about the performance.

---

