---
title: "Can't downgrade libgl1-mesa-glx"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by maze1216 on 2008-06-11
QUICK VERSION
accidently installed libgl1-mesa-glx ver. 7.0.3-1 need to take that file back to the original version that ubuntu was using. but it requires 3000 other programs to be removed in order to uninstall the current version... how do i downgrade that file without reinstalling the whole damn computer?


LONG VERSION

So in an attempt to install the new VegaStrike .5 I think, I ended up on the wrong page and found a list of dependent drivers needed for what i thought was the program.... so... i started installing them, figuring hell, half of ubuntu is beta anyway why not go all out. so i did, made it halfway down the list before i realized... hey, there's a 500 meg download of the program, i'll try that, got that, installed it, didn't work... needed libgl1-mesa-dri... so i checked, that somehow had been removed. so i went to put it back, told me it needed the same version of libgl1-mesa-glx to install that driver and i had a newer version (i presume beta) it was one of those files i had just installed a new version of. so i found all the rest of the libgl1-mesa-* files for version 7.0.3-1 and installed them.... although the game does now work...... it crashes at least every 5 minutes. my computer locks up every time my bluetooth mouse gives a battery low message and random things lock up the computer completely.. so.... i would really like to go back to the older version of libgl1-mesa-* but.. when i go to remove them, they tell me i have to remove roughly 3000 other programs in order to take out libgl1-mesa-glx........... so... how do i downgrade that file without wiping my whole installation???

---

### Post by Partyboi2 on 2008-06-11
Find the version of the package you want from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=libgl1-mesa-glx&searchon=names&suite=all&section=all"). Open a terminal (Applications>Accessories>Terminal) and cd to the directory of the downloaded package. Then install it with
```
sudo dpkg -i <package>
```it should downgrade to the package you want.

---

