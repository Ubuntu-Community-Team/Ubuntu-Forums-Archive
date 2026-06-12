---
title: "Trying to Install Native Spotify Client"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by fleamour on 2011-10-06
Just upgraded to Spotify Unlimited, trying to install I get this error:
```
The following packages have unmet dependencies.
 spotify-client-gnome-support : Depends: spotify-client-qt (= 1:0.5.2.84.g6d797eb-1) but 1:0.6.1.309.gb871a7d-1 is to be installed
E: Broken packages

```

What does this mean?

---

### Post by tgalati4 on 2011-10-06
Welcome to dependency hell.  If you are running Lucid, then perhaps only spotify-client-qt (= 1:0.5.2.84.g6d797eb-1) is available, but you need 1.0.6.

What is the output of:

apt-cache policy spotify-client-qt

You could try a force install, but that can lead to breakage.  Since it's doubtful that other programs would depend on spotify-client-qt, you can probably get a way with it.

---

### Post by fleamour on 2011-10-06
I'm running latest 11.04.
```
spotify-client-qt:
  Installed: (none)
  Candidate: 1:0.6.1.309.gb871a7d-1
  Version table:
     1:0.6.1.309.gb871a7d-1 0
        500 http://repository.spotify.com/ stable/non-free i386 Packages
```

---

### Post by tgalati4 on 2011-10-06
So you have the opposite problem.  The package that you downloaded relies on 1.05 but 11.04 has built 1.06.

So what is the output of:

apt-cache search spotify

---

### Post by david.trevelyan on 2011-10-07
Someone posted a link to the old spotify-client-qt package on getsatisfaction. It can be found [here]("http://www.easy-share.com/DC3BDA76EE5C11E09676002481FAD55A/spotify-client-qt_1:0.5.2.84.g6d797eb-1_amd64.deb"). I installed client-qt using dpkg and then installed the gnome support with apt-get. It works fine!

---

### Post by fleamour on 2011-10-07
@tgalati4

I cannot install the Spotify Client Gnome Support, however, output of apt-cache search spotify:

```
spotify-client-gnome-support - Spotify desktop gnome support
spotify-client-qt - Spotify desktop client
```

I was just following Spotify's official instructions but they make no mention of Gnome Client.  I believe it is needed to work though.  I Googled two different websites which chucked up same install error.

Is there a web page that hosts the most recent packages?  Seems like a simple error after all, but I must admit I cannot get my head around dependencies.  I must try harder!

---

### Post by fleamour on 2011-10-07
So should I downgrade client-qt then lock package version, then install Gnome Support?

---

### Post by fleamour on 2011-10-07
Damn, cannot force earlier version.

---

