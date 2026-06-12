---
title: "Need help installing VLC Media Player"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by glowstick on 2005-08-08
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

I'm new to linux and I want to install this media player but I have no idea what to do or what to install.

Any help I can get would be great, thanks.

---

### Post by kosmic on 2005-08-08
Go to System -> Administration -> Synaptic

Then in the Repositories section see if you have the Universe activated.

then just search for vlc

and press Apply to install VLC


For a introduction to ubuntu I think you sould have a look at -> [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Lord Illidan on 2005-08-08
I take it you have read the ubuntu guide?

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) 

Once you have added the repositories, you just need to do:

```
sudo apt-get install vlc
``` 

and enter your password.

Or else, fire up synaptic

```
sudo synaptic
``` 

and search for vlc, **AFTER**  you have added the repositories and done ```
sudo apt-get update
``` 

Cheers!

---

