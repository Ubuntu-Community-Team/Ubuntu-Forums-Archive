---
title: "OH MY GOsH.! Windows 7 just blocked my Ubuntu 9.10.!"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Edgar09 on 2010-02-15
Linux experts i need your help.
This morning i installed Windows 7 on an old Vista partition..

When i restated W7 i couldnt see the grub anymore.!! :-(
I defenitly sure that i did not replace ubuntu.! Damm stinkin windows.!! What can i do Linux experts help me pleasee.!!!

---

### Post by Megafag on 2010-02-15
> **Edgar09 said:**
> Linux experts i need your help.
This morning i installed Windows 7 on an old Vista partition..

When i restated W7 i couldnt see the grub anymore.!! :-(
I defenitly sure that i did not replace ubuntu.! Damm stinkin windows.!! What can i do Linux experts help me pleasee.!!!

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Follow the instructions on that, all your ubuntu stuff should be fine :)

---

### Post by darkod on 2010-02-15
This is a much better link for bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be careful if you have a clean install of 9.10 then you are using grub2, so follow the instructions for 9.10 and use a 9.10 cd. DO NOT execute commands for grub1!
For grub1 you need to use 9.04 cd and the instructions for 9.04 or earlier.

---

### Post by Megafag on 2010-02-15
> **darkod said:**
> This is a much better link for bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be careful if you have a clean install of 9.10 then you are using grub2, so follow the instructions for 9.10 and use a 9.10 cd. DO NOT execute commands for grub1!
For grub1 you need to use 9.04 cd and the instructions for 9.04 or earlier.

Oh crap i forgot he is probably using karmic...

Listen to this guy :)

---

### Post by wilee-nilee on 2010-02-15
> **darkod said:**
> This is a much better link for bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be careful if you have a clean install of 9.10 then you are using grub2, so follow the instructions for 9.10 and use a 9.10 cd. DO NOT execute commands for grub1!
For grub1 you need to use 9.04 cd and the instructions for 9.04 or earlier.

Great link the 1st part should do it. here is a link to a grub2 wiki as well.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by Edgar09 on 2010-02-15
Hurray.!!! i got ubuntu back.!:popcorn:
but....
Windows 7 isnt working anymore.?!
Now how can i get that back & have both 0S work without problems.?!

---

### Post by kansasnoob on 2010-02-15
While booted into Ubuntu run:

```
sudo update-grub
```

Wait for it to say done and hopefully you'll be able to boot both.

---

### Post by Edgar09 on 2010-02-15
Wow.! Just like that.! Ubuntu Rocks.!!
Thanks alot you guys.! 
All of You thk u.!
:popcorn:

---

