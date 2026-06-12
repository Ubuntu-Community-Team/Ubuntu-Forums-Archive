---
title: "Help, installing bittorrent"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2008-08-18
Not too sure about the linux terminal at the moment, I had a hard time with linux before which caused me to uninstall it. But now I have found a use for it. Anyway I need help installing bittorrent on this Operating System. I tried going to the directory where the linux source is(I think thats what its called) in the terminal then typing make install, however I get :

** no rule to make target "install" Stop.

Maybe I downloaded the wrong source, maybe I'm doing it incorrectly, any help would be wonderful.

---

### Post by tuxxy on 2008-08-18
Ubuntu comes with a bit torrent client if thats what you mean, try **applications > internet > transmission ** or if you fancy a more sophisticated client you could try Deluge, its in the repos or type

```
sudo apt-get install Deluge
```

---

### Post by mellowd on 2008-08-18
If you are new to linux I'd suggest to stay away from compiling anything at the moment. 

Are you a bit comfortable on the command line though? If so I'd reccomend using rtorrent as you can ssh into it from anywhere and use screen to manage it from anywhere

---

### Post by Jeremywilms on 2008-08-18
Oh I see, thank you, however for future reference, did I input the correct command or was it the source?

---

### Post by tuxxy on 2008-08-18
You must configure it first, by typing

```
./configure
```

then make,

```
make
```

finally install it, 

```
sudo make install
```

---

