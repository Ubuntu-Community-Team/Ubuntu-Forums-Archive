---
title: "Phatch &amp; F spot have changed for the worse since 9.10 installation"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by caedmon on 2009-11-27
Installed 9.10 with no problems but am finding the combination of F Spot & Phatch really irritating now. I sell online & process lots of images. 
Before, F Spot used to automatically locate them in the pictures file, labelled with the date and time. Now they go into a folder called 2009 and are only labelled with the day, ie just 27. If I upload another batch of photos without changing the label its dumps them in the same file, so I have to move them elsewhere.

Then Phatch batches them & puts them in a file on the desktop just called phatch. Previously it used to create a new file next to the original,handily and clearly labelled with the date date, time & phatch. 

It is really slowing me down & I wonder why it has changed when it worked so well before. I seem to spend half my life finding, moving & labelling images, when all this used to be done automatically before. Grrrr!

---

### Post by stani on 2009-12-10
Just the default folder value has changed for Phatch. You can revert to the old situation by giving the following value to 'In' in the save action:
```
<folder>_phatch/<subfolder>
```

---

