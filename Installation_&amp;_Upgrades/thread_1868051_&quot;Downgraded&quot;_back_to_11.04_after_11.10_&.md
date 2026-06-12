---
title: "&quot;Downgraded&quot; back to 11.04 after 11.10 &quot;upgrade&quot;"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by RudyG on 2011-10-23
Well after 2 days of wrestling with 11.10 and losing my perfectly configured 11.04 system. I had to wipe the 11.10 installation with a clean 11.04 install. It seems like Pulseaudio can no longer be uninstalled from 11.10 like it can be from 11.04. :(:confused: And since Pulseaudio does not support my sound card and never will, it looks like I'll be staying with 11.04 on my machine until it "expires".
A bit of a bummer as I'll be missing out on the 3.X kernel and 4.7.x KDE. But oh well. Can't really understand why the distributors change the Pulseaudio removal option. :( :confused:

Rudy

---

### Post by mrw on 2011-10-24
I downgraded back to 10.1. The new version is a disaster. If it's not broke why try and fix it?

---

### Post by Jaybyrrd on 2011-10-24
So I read this going NO WAY! They wouldn't do that, but nothing I can find in the way of removing it says otherwise. Maybe an update in the future will fix this?
 
And Oneiric is a disaster if you upgrade, a clean install is actually just fine.

---

### Post by RudyG on 2011-10-24
> **mrw said:**
> I downgraded back to 10.1. The new version is a disaster. If it's not broke why try and fix it?
Yup. 100% agree. Unfortunately when I was asked whether I wanted to update the system I mechanically answered yes. And my perfectly configured system was overwritten with 11.10.:( Oh well. Live and learn.
> **Jaybyrrd said:**
> So I read this going NO WAY! They wouldn't do that, but nothing I can find in the way of removing it says otherwise. Maybe an update in the future will fix this?
 
And Oneiric is a disaster if you upgrade, a clean install is actually just fine.I tried a clean install of 11.10 after the upgrade, with the same result.

However, there may be a lite at the end of the tunnel. I posed this question on the Kubuntu forum and was told to use:
```
sudo apt-get remove pulseaudio
```

Instead of Muon. Interesting that KPackageKit in 11.04 was able to remove Pulseaudio cleanly and Muon in 11.10 cannot. It removes too many dependencies.
Ahhh to see the day when Pulseaudio is shipped as an uninstalled option rather than forced upon us. :(

Anyway, I'll report back on what happens.
Rudy

---

### Post by Jaybyrrd on 2011-10-24
Is there no way to simply install a different software and simply disable Pulse? 

And my clean install actually works great so far, it was when I did an upgrade that life was miserable.

---

### Post by RudyG on 2011-10-25
OK it seems like Muon is not quite ready for prime time, although it's very close. It installs things just fine but removing stuff you have to be very careful as Muon will blow away system components, with no confirmation.:(

So I used:
```
sudo apt-get remove pulseaudio
``` to remove pulseaudio and it worked like a charm. Am typing this on fresh install of 11.10

Hope this helps someone.
Rudy

---

### Post by qamelian on 2011-10-25
> **Jaybyrrd said:**
> So I read this going NO WAY! They wouldn't do that, but nothing I can find in the way of removing it says otherwise. Maybe an update in the future will fix this?
 
And Oneiric is a disaster if you upgrade, a clean install is actually just fine.
Not for me. A clean install was impossible, but upgrading was smooth as silk. :)

---

### Post by Firem4nJoe on 2011-10-25
Fully agree 11.10 upgrade is a mess. I now use Showtell Photo Viewer because Image Viewer is now the slowest thing on the planet and so are many Firefox features but I tend to use Chrome anyway.

Also I miss the Classic View.
I don't suppose there's a quick easy way to downgrade/roll back to 11.04 without having to do a whole new clean install...?

---

