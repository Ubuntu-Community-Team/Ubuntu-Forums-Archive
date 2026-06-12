---
title: "What CDR's are best?"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by Toon81 on 2006-04-23
I was at a local convenience store the other day and noticed a bunch of CD-Rs on offer so I decided to get those since they were pretty cheap and I was out of CD-Rs. Having wanted to try out Ubuntu for a while now, I figured I mighjt give it a shot, so I downloaded the image, burned it and ran it and got a few strange errors. When I simply skipped the parts that gave me errors I had a workingm albeit slightly unstable, installation of Edubuntu (instead of the Ubuntu I downloaded). I had to redo the install for a different reason and it failed for yet another error, so I figured maybe I should redo burning the CD (at a slower speed).

It turns out my hunch seems correct, because now I burned a new CD (at 2x, couldn't burn slower than that) and it wouldn't let me set the password for my first user, so I just tried to install it *again* with the exact same CD and at "installing the base system" it gave me the error that Ubuntu "couldn't figure out how to install the base system"... Even though it had installed a fully functional base system half an hour earlier.

So just to rule out the possibility that my CD-Rs are bad, which are the best ones? How do I know which ones are not just suitable for burning audio CD's, but things like operating systems? I'm currently using Maxell ones that don't have a model name or number, but say that they can be used at speeds up to 52x. They come in a blue and green box, I got it here in the Netherlands.

---

### Post by Sef on 2006-04-23
> How do I know which ones are not just suitable for burning audio CD's, but things like operating systems?

Any CD-R that says data on it.

> so I figured maybe I should redo burning the CD (at a slower speed).

Don't burn at faster than 4x.  Otherwise corruption could happen.

> I had a workingm albeit slightly unstable, installation of Edubuntu (instead of the Ubuntu I downloaded)

One of two reasons for that:

1) You downloaded the wrong iso.

2) The mirror is set up wrong.

After downloading and before burning, did you do an md5sum check to make sure the iso downloaded right?  If you downloaded with bittorrent, it does it automatically.

---

### Post by Toon81 on 2006-04-23
No, the mirror is set up correctly. The first install of the image produced an Edubuntu installation, while the second produced an Ubuntu installation. I know it was the same image because I downloaded it twice and verified its MD5 sum against the MD5-sum list found at the mirror list at ubuntu.com; I recognized the MD5 sum the second time I checked it. I think the first one turned into an Edubuntu because I ran "apt-get update" because the installer told me it might fix an error message I got; I was too lazy to see what error message it was. At any rate, I am confident that the image was fine (as was the mirror) but I got an Edubuntu because of some mistake of mine. :)

The CD-Rs I use at the moment don't say "data" but they don't say "audio" either. Am I correct in understanding from your reply that all CD-Rs that say "data" can be used to provide reliable media to be used as linux installer CDs? I figured there might be some difference in quality between cheap and expensive ones; or is it like batteries, in that there are only like three factories in the world and all of them are really practically the same, only with a different label on them?

---

### Post by Sef on 2006-04-23
> The CD-Rs I use at the moment don't say "data" but they don't say "audio" either.

They would be data cds then.

> Am I correct in understanding from your reply that all CD-Rs that say "data" can be used to provide reliable media to be used as linux installer CDs?

Yes.

>  I figured there might be some difference in quality between cheap and expensive ones....

Not necessarily between cheap and expensive, but also between cheap and inexpensive.

Note: For the nonnative English speakers, there is a big difference between cheap and inexpensive:  Cheap means low price and low quality.  Inexpensive mean low price and high quality.

> is it like batteries, in that there are only like three factories in the world and all of them are really practically the same, only with a different label on them?

A number of factories make them, but since they are a mass market item, they are basically the same, although differences can exist in terms of quality.

---

