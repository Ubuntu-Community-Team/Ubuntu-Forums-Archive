---
title: "DVD Drive Loads CD to Sound Juicer, but doesn't mount"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by pdowling on 2007-05-11
Hi,

Recently upgraded to Feisty.  Went pretty well!  But I'm new to Linux and experiencing a problem I don't understand.

When I insert a music CD into my DVD drive the following occurs:
- Soundjuicer appears
- I am able to play the music
- An "audio disk" icon appears on my desktop

But I can't tell where it is mounting the CD to.  I need to know that (or know how to control it) as before I upgraded to Feisty I was using abcde to rip my CDs to FLAC and MP3 files.

On Edgy I edited my abcde.conf file to point to CDROM=/dev/hdb which worked.  I tried a couple of other things in /dev, but they didn't work.

Can someone point me to a tutorial or something so I understand what happens when I insert a CD/DVD and how the mounting and devices work?  I feel very much in the dark.

Thanks,

Peter

---

### Post by honeydew on 2007-05-11
*looks for a audio cd...*

okie.. for me it mounts to /media/cdrom0

I can create mp3 files by going to soundjuicer > hrmm.. actually thats weird.. it seems to allready have a profile under the edit section.. but.. I cant select it.. I even tryed creating a new mp3 file and had no luck..ladies + gentlemen.. I believe we have a bug...

---

### Post by stchman on 2007-05-14
> **pdowling said:**
> Hi,

Recently upgraded to Feisty.  Went pretty well!  But I'm new to Linux and experiencing a problem I don't understand.

When I insert a music CD into my DVD drive the following occurs:
- Soundjuicer appears
- I am able to play the music
- An "audio disk" icon appears on my desktop

But I can't tell where it is mounting the CD to.  I need to know that (or know how to control it) as before I upgraded to Feisty I was using abcde to rip my CDs to FLAC and MP3 files.

On Edgy I edited my abcde.conf file to point to CDROM=/dev/hdb which worked.  I tried a couple of other things in /dev, but they didn't work.

Can someone point me to a tutorial or something so I understand what happens when I insert a CD/DVD and how the mounting and devices work?  I feel very much in the dark.

Thanks,

Peter

Yes, it mounts the CD in /media/cdromX where X is the cdrom number starting at 0.  If you want to rip your CDs to mp3 then use my procedure.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This procedure uses Juicer.  I have never used abcde.

---

### Post by NJC on 2007-05-25
stchman;

Thanks! I followed the link from your webpage and it worked very well - none of the packages needed updating so all I really needed to do was enter the code under the mp3 profile. 

FWIW, I used the VBR mp3 code and send a sample output file to three different people all running XP. Everyone was able to play them with no problems.

---

### Post by stchman on 2007-06-04
> **NJC said:**
> stchman;

Thanks! I followed the link from your webpage and it worked very well - none of the packages needed updating so all I really needed to do was enter the code under the mp3 profile. 

FWIW, I used the VBR mp3 code and send a sample output file to three different people all running XP. Everyone was able to play them with no problems.

My XP did not play them until I installed a VBR plugin for WMP.

---

