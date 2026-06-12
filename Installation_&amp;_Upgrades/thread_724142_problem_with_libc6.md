---
title: "problem with libc6"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by k33bz on 2008-03-14
Ok this is the 3rd time I am having a problem with other packages recognizing this paticuliar package. Getting quite aggravated at it now. 

For my most recent problem I have just downloaded libzzip-0-13 (its a dependecy for a game i have) I go to run it and it tells me that the criteria isnt matched, that i need libc6, it looked familiar, so I didnt pay no mind to it. (as said 3rd time for this error).

Anyway, I go look up this library in the Synaptic manager, and what do i see, this package, libc6, is already installed.  But i have several programs that dont recognize it as installed,  How do i correct this?

---

### Post by {BzF}~JOKesTER on 2008-03-14
In Terminal:

sudo apt-get remove libc6 --purge

sudo apt-get autoremove

{Select Yes And Hit Enter}

sudo apt-get autoclean

sudo apt-get update

sudo apt-get install libc6

{If You Get An Error "Libc6 Not Found" Than In Synaptic - Go To Repositories And Check All Boxes In All Tabs - Might Need Your Install CD For This - Don't Have One Uncheck The CD's Under The First Tab Of Repositories}

Hope This Helps!! {If So Please Hit "Thanks" To Your Hearts Desire}

:)

---

### Post by NickEvans on 2008-03-14
Hmm that solution seems a little risky. Here's what helped me.

[http://ubuntuforums.org/showthread.php?t=684763](http://ubuntuforums.org/showthread.php?t=684763)

Hope it helps, I was terrified of hosing my system.

---

### Post by k33bz on 2008-03-15
> **{BzF}~JOKesTER said:**
> In Terminal:

sudo apt-get remove libc6 --purge

sudo apt-get autoremove

{Select Yes And Hit Enter}

sudo apt-get autoclean

sudo apt-get update

sudo apt-get install libc6

{If You Get An Error "Libc6 Not Found" Than In Synaptic - Go To Repositories And Check All Boxes In All Tabs - Might Need Your Install CD For This - Don't Have One Uncheck The CD's Under The First Tab Of Repositories}

Hope This Helps!! {If So Please Hit "Thanks" To Your Hearts Desire}

:)


I checked that at, luckily I didnt run it through, it would of uninstalled almost all of my packages.

---

