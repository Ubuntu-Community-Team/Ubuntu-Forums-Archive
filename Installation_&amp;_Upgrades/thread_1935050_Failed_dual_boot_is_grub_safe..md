---
title: "Failed dual boot is grub safe."
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by skitzer1 on 2012-03-03
:???:Hi all i am a complete novice to open source, i am going to install ubunto on its own drive hopefully using the hot swap with my docking station.However prior to this idea i had a failed attempt at a dual boot,with W7 as a primary O\S the grub loader loaded ok, just the ubunto 11.10 kernel failed as it was to big to load a mistake on my part.My worry now is?could this bootloader create any problems for my W7? using the hot swap? as i really dont want to loose this7.A freind of mine has been so kind and gave me a orignal very old copy of ubuntu with a large book called Ubuntu from novice to pro.For obvious reasons i really need to install this copy and build up the O\S to a fully functioning system.Could i loose 7 by using this method; is a hot swap classed as slave?As i have stated i am a novice these questions may seem trivial,but i dare any novice to state that ubuntu does not seem baffling in the begining.So did 7 when i first tried it!Thanks to any one for taking the time to read this and replying.Hopefully goodbye to viruses and hello Ubuntu.

---

### Post by dino99 on 2012-03-03
a little guide:  [http://ubuntuforums.org/showpost.php?p=11654218&postcount=3](http://ubuntuforums.org/showpost.php?p=11654218&postcount=3)

and more following the links below :)

---

### Post by darkod on 2012-03-03
So, right now they are installed on the same disk? Win7 and 11.10?

If you want to remove the ubuntu you will have to restore win7 bootloader to the MBR of that disk first. In case you don't have a win7 dvd boot your win7 and make a rescue cd. You can use that to install the windows bootloader on the MBR.

If you do this right now, ubuntu will stop booting since windows bootloader doesn't recognize it. So make sure you get out any data you want  from ubuntu first.

I have no idea what are you trying to do with the docking station. Is that like an external disk? You will plug a disk into it and it will be as external?

---

