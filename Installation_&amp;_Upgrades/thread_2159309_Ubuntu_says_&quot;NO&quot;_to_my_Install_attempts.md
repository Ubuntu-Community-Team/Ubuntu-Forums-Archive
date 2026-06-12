---
title: "Ubuntu says &quot;NO&quot; to my Install attempts"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by RoflWaffle17 on 2013-07-02
So, I have a brand new external harddrive that I would like to install ubuntu on. However it is turning out to be not as simple as that. I downloaded ubuntu 12.04 and used pendrivelinux to create a bootable flash drive in order to install it. I unplugged my internal SSD Drive as well as my internal HDD and only had my external hooked up, along with flash drive inserted. When it started it first asked me what language I wanted, and I selected English. Then it asked whether or not I want to try without install or install? I clicked install, because thats what I want to do!! Alas, it stopped on a black screen with a blinking underscore....I have heard from friends that this is normal on install and that it should only last like 4 minutes....well I gave it 4 minutes..and then some....and then some....roughly an hour, but nothing happened. So I was like well...maybe it is the version? so I did the same pendrivelinux conversion on the 13.04 iso. same problem. Then I was like well, maybe it's because I tried immediately installing it rather than trying it out (just trouble shooting, I didn't think this would make a difference, but I gave it a try). But still no go. Then I was like, maybe because I'm using a flash drive...so I tried my friends 12.04 live CD...still same thing. 

So, this leads me to believe that either it's a really technical software issue, or a hardware issue. Seeing as I just built my computer maybe a little over 2 weeks ago from complete scratch I don't see how it could be hardware, but I'm up for suggestions. Also, I am using Windows 7 Ultimate 64 bit...I know Windows 8 users have been having some issues with this, but like I said I'm using Windows 7. Any suggestion would be aweome! 

_**FYI the rundown of my comp includes (incase you guys think it is hardware related)**_
Mobo: Asus Z77 Sabertooth LGA 1155
CPU: Intel i5 LGA 1155 socket 3.4GHz
Video Card: EGVA Superclocked GTX 770
Corsair H100 Extreme Water Cooling
PSU: EVGA 1000w SuperNova
Windows OS SSD: Kingston 120gb Solid State
Storage Drive: Seagate Barracuda 1TB
External Drive : Seagate Slim 500gb <--The one I'm trying to eventually have Ubuntu installed on.

---

### Post by Bucky Ball on 2013-07-02
Welcome to the forums.

Boot as if to install from the dongle again, when you get to the screen that gives the options to try or install, hit F6. You should get some options. Choose 'nomodset'. Continue to try Ubuntu, NOT install, and see if you get to a desktop.

---

### Post by RoflWaffle17 on 2013-07-02
If this works and I successfully "try" ubuntu should I go ahead and click the install setup app on the desktop of the trial ubuntu?

---

### Post by Bucky Ball on 2013-07-02
Don't see why not, if you like what you see. If you have major issues everywhere might be best to post here first, but it is hard to know until it is on the hard drive. Some device drivers can't really be installed running from the LiveCD. 

You can get online from the 'Try' desktop with a cable (or if you're lucky wifi). Stick it in before booting.

---

### Post by sudodus on 2013-07-02
> **Bucky Ball said:**
> Welcome to the forums.

Boot as if to install from the dongle again, when you get to the screen that gives the options to try or install, hit F6. You should get some options. Choose 'nomodset'. Continue to try Ubuntu, NOT install, and see if you get to a desktop.
+1 try to use the boot option 'nomodset' and try Ubuntu

> **RoflWaffle17 said:**
> If this works and I successfully "try" ubuntu should I go ahead and click the install setup app on the desktop of the trial ubuntu?

Yes, provided you have enough memory. I think you forgot to specify how much you have, but I am rather sure you have more than 1 GB.

> **Bucky Ball said:**
> Don't see why not, if you like what you see. If you have major issues everywhere might be best to post here first, but it is hard to know until it is on the hard drive. Some device drivers can't really be installed running from the LiveCD. 

You can get online from the 'Try' desktop with a cable (or if you're lucky wifi). Stick it in before booting.
+1
-----
- Did you check the md5sum of the downloaded iso file? 

- You may have better luck with Unetbootin.

- But I think it is a problem with the graphics driver.

---

### Post by RoflWaffle17 on 2013-07-03
> **sudodus said:**
> +1 try to use the boot option 'nomodset' and try Ubuntu



Yes, provided you have enough memory. I think you forgot to specify how much you have, but I am rather sure you have more than 1 GB.


+1
-----
- Did you check the md5sum of the downloaded iso file? 

- You may have better luck with Unetbootin.

- But I think it is a problem with the graphics driver.

Yeah, if all goes well, i'll be installing on a 500gb external drive...and would ike to allocate 8-10 of that towards the ram.

---

### Post by sudodus on 2013-07-03
If you intend to hibernate, you need slightly more swap than RAM, otherwise you probably get along well with 1-2 GB swap. The exception is if you intend to run some very memory-intensive programs, but new computers today have enough RAM for most applications to avoid heavy swapping.

---

### Post by Bucky Ball on 2013-07-03
> **RoflWaffle17 said:**
> Yeah, if all goes well, i'll be installing on a 500gb external drive...and would ike to allocate 8-10 of that towards the ram.

Not sure I understand. Do you mean 8-10Gb toward RAM or for a /swap partition? Depending on your setup and if you are doing this for a reason there's no point. 2Gb is fine unless you're intending to do a lot of hibernating with a lot of things open, in which case the old rule of thumb is /swap = double your RAM. Everyone has a theory on this. ;)

---

