---
title: "hardy: gimp?"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by stephan0h on 2008-07-24
Hello,

Upgraded from gutsy to hardy (8.04) - now gimp is broken.

First I wondered, why gimp was gone, then, when trying to reinstall the package seemed to be broken. Is this a known bug?

regards,
stephan

---

### Post by mbsullivan on 2008-07-24
Gimp should work under Hardy (Note: I'm not running KUbuntu, so perhaps this doesn't hold for you, but I think it does). How is it broken (i.e. what's happening)?

What have you tried to reinstall, something like:

```
sudo aptitude reinstall gimp gimp-data libgimp2.0
```

??? And what was the error message?

Mike

---

### Post by stephan0h on 2008-07-25
I have tried this one which led to some conflicts:

sudo apt-get install gimp

Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  gimp: Hängt ab: libgimp2.0 (>= 2.4.6) aber 2.4.5-1ubuntu2 soll installiert werden
        Hängt ab: libpango1.0-0 (>= 1.20.5) aber 1.20.1-1 soll installiert werden
E: Kaputte Pakete

... it's German but I think you can grasp the meaning.

Tried your command but also didn't work ...

thanks,
 stephan

---

### Post by mbsullivan on 2008-07-25
Hi stephan,

It looks like you have some dependencies there that are preventing you from installing gimp...

Try reinstalling libgimp2.0 and libpango1.0-0 with the Hardy versions:

```
sudo aptitude -t hardy reinstall libgimp2.0 libpang01.0-0 gimp
```

Also, post your /etc/apt/preferences file so that we can find out why these weren't updated properly?

Mike

---

### Post by stephan0h on 2008-07-25
thanks, this worked.

Other than that I don't seem to have a /etc/apt/preferences file. should i have one?

thanks,
stephan

---

### Post by mbsullivan on 2008-07-25
Hmmm... Must not be the problem, then. The /etc/apt/preferences file can be used for "apt-pinning", by which you can force certain packages to install under a release. I had thought that perhaps your default pin was set to still be Gutsy, and that's why not all of your libraries upgraded to Hardy.

If you want to play it safe, then just leave everything as it is. Otherwise, you could try and create an /etc/apt/preferences file like the following:

```
Package: *
Pin: release a=hardy
Pin-Priority: 500
```

Then do a:

```
sudo aptitude update; sudo aptitude upgrade
```

To (I think) bring all of your packages to their Hardy equivalents. Might break stuff, though!

Mike

---

### Post by Sef on 2008-07-26
If you are using Kubuntu, then you want to use  **kdesu** instead of sudo.

---

### Post by mbsullivan on 2008-07-26
> If you are using Kubuntu, then you want to use kdesu instead of sudo.

Only for graphical applications, really. Unless I'm mistaken, kdesu is more analogous to gksu rather than sudo. Sudo should work fine from the terminal for KDE users.

Mike

---

