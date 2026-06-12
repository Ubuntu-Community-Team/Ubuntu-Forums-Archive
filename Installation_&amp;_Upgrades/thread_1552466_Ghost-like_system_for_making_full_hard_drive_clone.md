---
title: "Ghost-like system for making full hard drive clones to a network location"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by hashbrowns on 2010-08-13
Whenever I'm dealing with large numbers of computers that need to have identical windows installations put on them, I love using Symantec/Norton Ghost to image the NTFS partition (just making the .gho file the size of the disk I've used, instead of the 160/320GB full volume size), and then uploading it automatically to a windows share.

I'd love to be able replicate this exact process with Ubuntu. I have one computer that's ready to go, and a few dozen more that I'd like to quickly get that same image on.

I've heard that there's a command called **dd **that can make disk images, but I'd really like some sort of boot disk that can allow me to make an image, save it, then run the boot disk on another computer to allow me to reconnect to the server and dump that image on that computer. Ghost 4 Linux doesn't have a network/server component, I think.

even if such solutions cost money, I'd love to know if they exist or not.

---

### Post by Manyette on 2010-08-13
> **hashbrowns said:**
> Whenever I'm dealing with large numbers of computers that need to have identical windows installations put on them, I love using Symantec/Norton Ghost to image the NTFS partition (just making the .gho file the size of the disk I've used, instead of the 160/320GB full volume size), and then uploading it automatically to a windows share.

I'd love to be able replicate this exact process with Ubuntu. I have one computer that's ready to go, and a few dozen more that I'd like to quickly get that same image on.

I've heard that there's a command called **dd **that can make disk images, but I'd really like some sort of boot disk that can allow me to make an image, save it, then run the boot disk on another computer to allow me to reconnect to the server and dump that image on that computer. Ghost 4 Linux doesn't have a network/server component, I think.

even if such solutions cost money, I'd love to know if they exist or not.

You are looking for Clonezilla.  Exact fit for your needs!

---

### Post by hashbrowns on 2010-08-14
> **Manyette said:**
> You are looking for Clonezilla.  Exact fit for your needs!

Thanks! :) After doing some reading on it and checking out the screenshots, looks like it could indeed be exactly what I'm looking for. I'll check it out at work after the weekend's over!

---

