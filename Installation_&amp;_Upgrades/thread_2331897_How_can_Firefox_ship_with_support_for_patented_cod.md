---
title: "How can Firefox ship with support for patented codecs?"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by darknessdescends on 2016-07-26
Forgive the formatting of the post. I intended to list one codec per line, but I can't insert line breaks into my posts for some reason.  When Ubuntu 14.04 is installed, even if I unchecked the box "Install this third-party software" during the installation process, it includes support for a lot of patented codecs under Edit --> Preferences --> Applications. Here is a partial list:   ```
 Content that uses VLC plugin: ANX file AXA file AXV file MIDI audio MP3 audio MPEG video Ogg Audio Ogg multimedia file Ogg video WAV audio WebM video  Windows Media Player: ASF video ASF video AVI video Microsoft ASX playlist Windows Media audio WIndows Media video   QuickTime plugin: MPEG-4 video QuickTime video 
```  I was under the impression that if I unchecked that box, Ubuntu would NOT install patented codecs by default. Yet with this exttensive list, it seems quite likely at least some of these codecs are patented.  Does anyone know why?

---

### Post by mc4man on 2016-07-26
It's not FF which only provides the openh264 plugin, it's the totem-mozilla plugin. I'd guess that on a fresh install that totem plugin would do virtually nothing until the user installed various supporting libraries. So you have the means but not the way.
Also what you may have been looking for is shown here - 
[http://askubuntu.com/questions/426160/what-is-the-free-software-only-option-when-installing-ubuntu](http://askubuntu.com/questions/426160/what-is-the-free-software-only-option-when-installing-ubuntu)

---

### Post by grahammechanical on 2016-07-26
I guess it all depends on the licensing. Patents and copy-right are not necessarily evil in themselves. They stop someone else taking your intellectual property and patenting it or copy-righting it in their own name. The use you allow others to make of your property would be defined in the license agreement.

Another factor to consider is the great variety of legislation in this area around the world. What is legal in one country is not necessarily legal in another country. This would influence any decision on whether to classify a certain codex as suitable for inclusion in the default install or should be listed as third party software.

It seems that the ogg format is not patented.
> 
The creators of the Ogg format state that it is unrestricted by [software patents]("https://en.wikipedia.org/wiki/Software_patent")[SUP][[2]]("https://en.wikipedia.org/wiki/Ogg#cite_note-2")[/SUP] and is designed to provide for efficient [streaming]("https://en.wikipedia.org/wiki/Streaming_media") and manipulation of high quality [digital multimedia]("https://en.wikipedia.org/wiki/Digital_multimedia").

Because the format is free, and its reference implementation is not subject to restrictions associated with [copyright]("https://en.wikipedia.org/wiki/Copyright"), Ogg's various codecs have been incorporated into a number of different free and [proprietary]("https://en.wikipedia.org/wiki/Proprietary_software") [media players]("https://en.wikipedia.org/wiki/Media_player_%28application_software%29"), both commercial and non-commercial, as well as [portable media players]("https://en.wikipedia.org/wiki/Portable_media_player") and [GPS]("https://en.wikipedia.org/wiki/GPS") receivers from different manufacturers.

[https://en.wikipedia.org/wiki/Ogg](https://en.wikipedia.org/wiki/Ogg)

Regards

---

### Post by mc4man on 2016-07-26
From a 'discussion' standpoint there are no patent encumbered codecs in regards to _end users_. As an end user if you attempted to purchase a personal use license from any of the major licensing authorities you'd have no success. 
So it's purely a personal choice based on I don't know what as I personally choose to use them all.
(- though people can & should do as they please in these matters

---

### Post by darknessdescends on 2016-07-29
It's too late to do a full reinstall now. I will try to just uninstall the relevant packages. I got rid of totem-mozilla, but most, if not all of the codecs are still listed in Firefox. What else am I missing?

---

### Post by mc4man on 2016-07-29
> **darknessdescends said:**
> It's too late to do a full reinstall now. I will try to just uninstall the relevant packages. I got rid of totem-mozilla, but most, if not all of the codecs are still listed in Firefox. What else am I missing?
Listed where? In Tools > Add-on > Plugins most should be gone. Totem-mozilla installs 4, rhythmbox-mozilla 1.
screen with both removed, click on 'More' of any installed to find from where.

---

### Post by darknessdescends on 2016-07-30
Oh that's not the section I had in mind. Go to Edit > Preferences > Applications. You will see all the ones I listed in my original post.

---

