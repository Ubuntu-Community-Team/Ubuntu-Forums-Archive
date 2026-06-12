---
title: "Problem installing directly from the hard , not the cd .."
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by almasry on 2007-02-24
Hello guys ,

I want to setup Ubuntu directly from the Hard disk , From C partition ..
what I want to do , Is to make the installation manager starts from the HD drive , not the cd, as my CD is very slow  ..

I copied all the files and folders from the CD face , and placed them on the C partition face .. and edited a boot.ini file and wrote this peice of code :
> 
[boot loader]

timeout=10
default=c:\ 

[operating systems]
c:\ ="Ubuntu Setup" 
D:\ ="Windows Xp .." 


it succeeded booting  from the C partition, and the option was listed .., but when i click enter , it restarts instead of loading the boot screen ..
i tried replacing the first boot option to the  path "c:\"  and pointed it to some files, one "c:\install" and tried "c:\isolinux"  , but no answer ...

I know that there is some file responsible for the operation of loading the first boot screen which appears in the CD, but i can't define it ...

if someone could help me solving this problem , i would be so thankful ..

---

