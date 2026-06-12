---
title: "can't install mozilla-mplayer pkge"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by miek on 2006-03-25
Hi folks,
Have an issue with mozilla-mplayer just can't install it. trying to install it i get this error:
The following packages have unmet dependencies:
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) but it is not installable or
                            mplayer-custom (>= 1.0-pre5) but it is not installab le or
                            mplayer-386 (>= 1.0-pre5) but it is not installable or
                            mplayer-586 (>= 1.0-pre5) but it is not installable or
                            mplayer-686 (>= 1.0-pre5) but it is not installable or etc......

I did apt-get update and tried again with apt-get -f install .. same error.

My repository source list file can be found here: [http://paste.ubuntu-nl.org/10756](http://paste.ubuntu-nl.org/10756)

thanks for helping

---

### Post by jrib on 2006-03-25
add `` multiverse'' to the end of lines 6 and 7 and then ```
sudo apt-get update
```

---

### Post by miek on 2006-03-25
[QUOTE=_jason]add `` multiverse'' to the end of lines 6 and 7 and then ```
sudo apt-get update
```[/QUOTE]

Thanks it worked out.

---

