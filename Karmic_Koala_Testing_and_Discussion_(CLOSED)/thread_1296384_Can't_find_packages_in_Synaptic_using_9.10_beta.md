---
title: "Can't find packages in Synaptic using 9.10 beta"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2009-10-20
I have been looking at the 9.10 beta but am having difficulty in locating packages in Synaptic.  I was looking for the Mozilla-mplayer, flashplugin-nonfree and restricted extras but none would respond when searched for.

Could this be because I am working with 9.10 as a live CD?

I needed all the packages to let me listen to the various BBC radio & TV programmes that I am adicted to.

Your guidance will be appreciated

---

### Post by mike555 on 2009-10-20
perhaps yes , most programs wont install to a live cd , even in RAM ..........

---

### Post by mc4man on 2009-10-20
Go to System -> Admin.. -> Software Sources and disable the 'cdrom' source and enable all the ubuntu software sources

You may want to not install the restricted extras, just enable the needed packages thru synaptic ( will save space which is limited to available ram

( you can also clean out the downloaded .deb's in /var/cache/apt/archives/ after installing packages to gain some space (ram) back

---

### Post by Scunnered on 2009-10-20
My thanks to you both.

Will have a look at your suggestions and see what develops.  I was using 9.10 to show a friend how she could safely bank using Ubuntu live CD and started seeing how it would look and listen for me.

Will advise later on

Thanks again

Matter fully resolved when I loaded the release candidate.

---

