---
title: "Ubuntu 9.4. Where can I get the w64codec package"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by odror on 2009-04-04
Hi

I have just installed ubuntu 9.4 (mythbuntu 9.4) I installed 64 bit version.. How do I get the restricted codecs installed.

I.e. w64codec,libdvdcss2 and others. The direction for ubuntu 8.10 do not workl for this new version of ubuntu.

thanks

---

### Post by wolfen69 on 2009-04-04
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

you can now download anything. cheers.

---

### Post by taavikko on 2009-04-04
Haven't found one file that needs w{32,64}codecs to be installed.
Just to remind that that package also needs some form of application that knows how to read those codecs (mplayer, gstreamer-pitfdll)

But IMHO, w*codecs is an obsolete package.

decss library can be installed without medibuntu too.

```
sudo apt-get install libdvdread4 build-essentials && sudo /usr/share/doc/libdvdread4/install-css.sh
```

libdvdread4 is bundled in ubuntu-restricted-extras meta-package, so need to install separately. this way it also provides support for all kinds of media files,
thus makin w*codecs obsolete.

---

