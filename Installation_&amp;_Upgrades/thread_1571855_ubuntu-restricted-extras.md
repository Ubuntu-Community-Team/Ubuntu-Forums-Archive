---
title: "ubuntu-restricted-extras"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by mrwicked on 2010-09-10
hi! i am new to ubuntu.i downloaded ubuntu 10.04 dekstop edition n installed it from the cd . i need to install ubuntu-restricted-extras. where can i get it from. the problem is that i don't have internet connectivity on my ubuntu laptop, so i need an offline installer.please let me know if any download link is available. thanx!

---

### Post by ibod on 2010-09-10
Hi

I had the same problem and spent some time looking for an answer 
I did not find one (this does not mean there is not a way I am also quite new to ubuntu)
In the end it was quicker and Much easer to bring the PC to the Internet and just do it in a terminal 

You could look here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) -  for more ways to install but the terminal really is easy  

Easy one command :-   goto Applications> Accessories> Terminal> and paste the command below
sudo apt-get install ubuntu-restricted-extras

---

### Post by lechien73 on 2010-09-10
You can download the packages individually from:

[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

However, there are so many files and dependencies, that it would be difficult to install without access to the Internet.

Googling **ubuntu restricted extras offline installer download** gives plenty of supposed sources for offline installers, but I would be cautious about downloading any of them.

---

### Post by sikander3786 on 2010-09-10
Carry your PC where there is internet access. It will be easier.

Do you have access to any Ubuntu PC with internet access somewhere around you? If so you can install ubuntu-restricted-extras on that PC and then transfer it using APTonCD to your home PC.

Downloading from [http://packages.ubuntu.com](http://packages.ubuntu.com) won't help because every single file has got lots of dependencies. Downloading each of them is not possible.

---

### Post by mrwicked on 2010-09-10
> **sikander3786 said:**
> Carry your PC where there is internet access. It will be easier.

Do you have access to any Ubuntu PC with internet access somewhere around you? If so you can install ubuntu-restricted-extras on that PC and then transfer it using APTonCD to your home PC.

Downloading from [http://packages.ubuntu.com](http://packages.ubuntu.com) won't help because every single file has got lots of dependencies. Downloading each of them is not possible.

actually i have a dial-up connection. i have ubuntu/xp dual boot.
once i installed ubuntu under virtual box. so when i connected to the internet, it provided connectivity to ubuntu. so i guess if i download the packages in ubuntu under virtual box, i'll be able to use AptonCd. is it gonna work? do reply;)

---

### Post by mrwicked on 2010-09-10
> **sikander3786 said:**
> Carry your PC where there is internet access. It will be easier.

Do you have access to any Ubuntu PC with internet access somewhere around you? If so you can install ubuntu-restricted-extras on that PC and then transfer it using APTonCD to your home PC.

Downloading from [http://packages.ubuntu.com](http://packages.ubuntu.com) won't help because every single file has got lots of dependencies. Downloading each of them is not possible.

actually i have a dial-up connection. i have ubuntu/xp dual boot.
once i installed ubuntu under virtual box. so when i connected to the internet, it provided connectivity to ubuntu. so i guess if i download the packages in ubuntu under virtual box, i'll be able to use AptonCd. is it gonna work? do reply;)

---

### Post by howefield on 2010-09-10
> **mrwicked said:**
> actually i have a dial-up connection. i have ubuntu/xp dual boot.
once i installed ubuntu under virtual box. so when i connected to the internet, it provided connectivity to ubuntu. so i guess if i download the packages in ubuntu under virtual box, i'll be able to use AptonCd. is it gonna work? do reply;)

Sure, (assuming the Ubuntu VM version is also 10.04) or simply copy the package files over, once downloaded you'll find them in...

```
/var/cache/apt/archives
```

---

### Post by dv3500ea on 2010-09-10
[keryx]("http://keryxproject.org/") may be what you're looking for.

---

### Post by sikander3786 on 2010-09-10
> **mrwicked said:**
> actually i have a dial-up connection. i have ubuntu/xp dual boot.
once i installed ubuntu under virtual box. so when i connected to the internet, it provided connectivity to ubuntu. so i guess if i download the packages in ubuntu under virtual box, i'll be able to use AptonCd. is it gonna work? do reply;)
It surely will. You can use APTonCD or copy from /var/cache/apt/archives as howefield suggested.

---

### Post by mrwicked on 2010-09-11
> **dv3500ea said:**
> [keryx]("http://keryxproject.org/") may be what you're looking for.

keryx is supercool... thanx!!! now i am able to install everything i need.
thanx again

---

### Post by mrwicked on 2010-09-11
> **sikander3786 said:**
> It surely will. You can use APTonCD or copy from /var/cache/apt/archives as howefield suggested.

thanx for that APTonCD suggestion. but for now keryx is going perfectly fine for me. i'd surely use APTonCD someday

---

