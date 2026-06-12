---
title: "Ubuntu not recognizing all my RAM"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by rmills1 on 2010-10-02
I recently setup a new system with Ubuntu 10.04 64 bit.  I installed 4gb or ram (2x2gb) but Ubuntu only shows 3.4gb.  What do I need to do to get it to recognize all the memory?

---

### Post by PRC09 on 2010-10-02
If you have onboard video subtract it from the total amount of ram you have.Some is used by the system itself as well but I am not sure how much so that would be subtracted as well.Mine with 4gb reports 3.6...

---

### Post by rmills1 on 2010-10-02
> **PRC09 said:**
> If you have onboard video subtract it from the total amount of ram you have.Some is used by the system itself as well but I am not sure how much so that would be subtracted as well.Mine with 4gb reports 3.6...

Ahhh... thank you.  That makes perfect sense now that I think about it.  Makes me want to go out and buy a video card  :)

---

### Post by mörgæs on 2010-10-02
Good. Please mark the thread 'solved'.

---

### Post by Duckblaster on 2010-10-02
64 bit should show all the ram, only 32 bit shows less than 4 gb, are you sure it's 64 not 32 bit?

---

### Post by rmills1 on 2010-10-03
> **Duckblaster said:**
> 64 bit should show all the ram, only 32 bit shows less than 4 gb, are you sure it's 64 not 32 bit?

Well I thought I was sure until you asked and I realized I didn't know how to confirm that.

Here's the mobo I bought: [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128394&Tpk=GIGABYTE%7CGA-MA785GM"), [cpu]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687")

The cpu says it supports 64bit.  Does that mean it defaults to 32bit and I need to configure something?

---

### Post by jocko on 2010-10-03
> **rmills1 said:**
> Well I thought I was sure until you asked and I realized I didn't know how to confirm that.

Here's the mobo I bought: [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128394&Tpk=GIGABYTE%7CGA-MA785GM"), [cpu]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687")

The cpu says it supports 64bit.  Does that mean it defaults to 32bit and I need to configure something?

Not sure why, but I think some of your "lost" memory is just a matter of definition.
According to the classic definition, 1kB is 2^10 B=1024 B, 1 Mb is 2^20 B=1024kB and so on. That would mean 8 Gb is 8192 Mb or 8388608 kB, but by some reason my "8 GB" is only 8186184 kB (=7.8 GB). So if you have "4 GB" memory ubuntu will report 3.9.

The rest of your missing memory is the part of RAM which is dedicated to your onboard video chipset. I found in your motherboard manual that you can set it to use either 128, 256 or 512 MB. If you dedicate 512 MB to video, ubuntu will only see 3.9-0.5=3.4 GB. If you want a little bit more RAM you can always lower the amount dedicated to video, or get a real graphics card with it's own memory and disable the onboard video chipset...

---

### Post by rmills1 on 2010-10-03
> **jocko said:**
> Not sure why, but I think some of your "lost" memory is just a matter of definition.
According to the classic definition, 1kB is 2^10 B=1024 B, 1 Mb is 2^20 B=1024kB and so on. That would mean 8 Gb is 8192 Mb or 8388608 kB, but by some reason my "8 GB" is only 8186184 kB (=7.8 GB). So if you have "4 GB" memory ubuntu will report 3.9.

The rest of your missing memory is the part of RAM which is dedicated to your onboard video chipset. I found in your motherboard manual that you can set it to use either 128, 256 or 512 MB. If you dedicate 512 MB to video, ubuntu will only see 3.9-0.5=3.4 GB. If you want a little bit more RAM you can always lower the amount dedicated to video, or get a real graphics card with it's own memory and disable the onboard video chipset...

Thanks jocko.  I figured it wasn't going to show as 4GB because of what you first said but I didn't think it would be as low as 3.4.  It makes sense that it's my video.  At least I know I'm getting 64bit support though.  I'll look into a graphics card.

---

### Post by nlsthzn on 2010-10-03
I would put money on it that you are running a 32-bit version of Ubuntu.

To see and have the benefit of all your RAM you will have to go 64-bit...

---

### Post by nikefalcon on 2010-10-03
> I would put money on it that you are running a 32-bit version of Ubuntu.
rmills1 explicitly mentions that he installs 64bit ubuntu.
IMO the explanations provided by jocko and the others are sufficient.

Please mark the thread as "solved".

---

### Post by nlsthzn on 2010-10-03
> **nikefalcon said:**
> rmills1 explicitly mentions that he installs 64bit ubuntu.
IMO the explanations provided by jocko and the others are sufficient.

Please mark the thread as "solved".

The explanations would only be valid if a 32-bit OS is installed as 32-bit OS's can only allocate up to 4GB of memory address spaces and thus you have to subtract the video memory from the RAM... in a 64-bit OS this is not the case...

So, if the OP definitely has a 64-bit version installed I find it odd as I have 64-bit Ubuntu 10.04 installed and my memory is showing as 3.9GB (as has been explained this is due to rounding of 1024 to 1000)... definitely not 3.6...

---

### Post by PRC09 on 2010-10-03
> The explanations would only be valid if a 32-bit OS is installed as 32-bit OS's can only allocate up to 4GB of memory address spaces and thus you have to subtract the video memory from the RAM... in a 64-bit OS this is not the case...

If this statement is true then where does the ONBOARD video get its SHARED memory from????? Just curious.Either in 32bit or 64....

---

### Post by nlsthzn on 2010-10-03
> **PRC09 said:**
> If this statement is true then where does the ONBOARD video get its SHARED memory from????? Just curious.Either in 32bit or 64....

Oops... yes, on-board graphics grabbing some RAM is a different matter all together and one I clearly miss-read in the previous posts and I do apologies...

---

### Post by Claus7 on 2010-10-03
Hello,

I have exactly the same problem with ubu 10.10, 32 - bit memory 4GB, showing only 3.4GB.

Two things though that I have not cleared yet: 

1) How someone subtracts the amount of memory from the graphics card?
And can this be done in 32 bit? Is this safe?

2) I cannot understand the fuss about 32 and 64 bit about the OP's system. A uname -a command would solve this issue pretty easily.

Regards!

---

### Post by nlsthzn on 2010-10-04
> **Claus7 said:**
> Hello,

I have exactly the same problem with ubu 10.10, 32 - bit memory 4GB, showing only 3.4GB.

Two things though that I have not cleared yet: 

1) How someone subtracts the amount of memory from the graphics card?
And can this be done in 32 bit? Is this safe?

2) I cannot understand the fuss about 32 and 64 bit about the OP's system. A uname -a command would solve this issue pretty easily.

Regards!

1) A 32-bit OS can only allocate address to 4GB of memory... so say your graphics card has 512MB of RAM and the system has 4GB it will allocate addresses to make it usable to the 512MB of graphics card and up to 3.5GB of RAM thus you will end up with 512MB of unusable RAM on the system... (if the graphics card has 1GB RAM you will loose out on 1GB of RAM)

2) Only I made a fuss thinking the OP is running 32-bit when he is in fact running 64-bit but his system is sharing RAM to the graphics card (something very different than the scenario in 1 above)...

---

### Post by Claus7 on 2010-10-04
Hello,

> **nlsthzn said:**
> 1) A 32-bit OS can only allocate address to 4GB of memory... so say your graphics card has 512MB of RAM and the system has 4GB it will allocate addresses to make it usable to the 512MB of graphics card and up to 3.5GB of RAM thus you will end up with 512MB of unusable RAM on the system... (if the graphics card has 1GB RAM you will loose out on 1GB of RAM)

2) Only I made a fuss thinking the OP is running 32-bit when he is in fact running 64-bit but his system is sharing RAM to the graphics card (something very different than the scenario in 1 above)...

thank you very much for your comprehensible response. Now it makes perfect sense. Just to point out that it was not so clear that, searching the web. Think this will be a reference point for others as well. 

With simple maths that means that the ram of my graphics card is 512MB. I had the impression that I had the 1GB version of such a card. I will check further.

Regards!

---

### Post by cascade9 on 2010-10-04
> **jocko said:**
> Not sure why, but I think some of your "lost" memory is just a matter of definition.
According to the classic definition, 1kB is 2^10 B=1024 B, 1 Mb is 2^20 B=1024kB and so on. That would mean 8 Gb is 8192 Mb or 8388608 kB, but by some reason my "8 GB" is only 8186184 kB (=7.8 GB). So if you have "4 GB" memory ubuntu will report 3.9.

The system tneds to reserve some RAM, and use some RAM for all the onboard stuff (network, sound, etc). That is why you get 7.8GB, not 8GB.

> **nlsthzn said:**
> So, if the OP definitely has a 64-bit version installed I find it odd as I have 64-bit Ubuntu 10.04 installed and my memory is showing as 3.9GB (as has been explained this is due to rounding of 1024 to 1000)... definitely not 3.6...

3.9GB is nothing to do with the 1024/1000 GB/GiB nonsense. All RAM is sold in 'binary' MB/GB (aka MiB/GiB), not 'decimal' MB/GB.

---

