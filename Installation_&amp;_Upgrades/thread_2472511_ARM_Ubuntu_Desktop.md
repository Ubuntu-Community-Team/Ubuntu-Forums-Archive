---
title: "ARM Ubuntu Desktop"
date: 2022-03-01
forum: Installation &amp; Upgrades
---

### Post by zkab on 2022-03-01
Can I install & run Ubuntu desktop 21.10 on an ARM computer without any issues?

---

### Post by grahammechanical on 2022-03-01
There are Ubuntu 21.10 Server images for ARM but not Desktop images.

[https://ubuntu.com/#download](https://ubuntu.com/#download)

When 22.04 is released there will be Ubuntu Core 22 images for ARM but they do not come with a desktop. As for issues, it will depend upon the version of the ARM CPU that you are using and whether or not it is supported.

Regards

---

### Post by zkab on 2022-03-01
OK ... thanks

---

### Post by TheFu on 2022-03-01
Not all programs have been ported to ARM, but I bet over 90% have, perhaps 95-99%. IDK.  Last time I looked, a key program that I needed was not ported, so I got an x86-64 CPU instead.

If ARM ever takes off for desktop use, then more and more programs, and more importantly, the libraries used by those programs will be ported. Nothing bad about ARM, except that for a while now, they have been fairly low-end CPUs, except the proprietary Apple version.

---

### Post by MAFoElffen on 2022-03-05
I have Ubuntu Desktop installed on ARM hardware... That I have installed on systems I installed from the Ubuntu Server (ARM) Live installer.

After installing minimal server, after reboot, then 
```

sudo update
sudo apt install ubuntu-desktop

```
Are there things you still have to do after that? Yes. Is it out-of-the-box? No. I can work, but with work.

Such as, on most ARM hardware, that ARM hardware does not support 'VGA' as any standard for graphics, so you have to use FrameBuffer as the graphic type and drivers.

I can talk to more on that if you decide to try that.

---

### Post by him610 on 2022-03-05
@zkab
You may want to consider armbian, [https://www.armbian.com/]("https://www.armbian.com/")
Downloads are available for both server and desktop.

---

### Post by kurt18947 on 2022-03-06
Maybe I'm missing something but Raspberry Pi is a pretty popular ARM based device. This seems pretty straight forward. What isn't straight forward right now is getting a higher spec Raspberry Pi for a reasonable price.

[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

I've thought about getting a Pi for use as a torrent server thingy, given that they use very little power.

---

### Post by MAFoElffen on 2022-03-06
> **kurt18947 said:**
> Maybe I'm missing something but Raspberry Pi is a pretty popular ARM based device. This seems pretty straight forward. What isn't straight forward right now is getting a higher spec Raspberry Pi for a reasonable price.

[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

I've thought about getting a Pi for use as a torrent server thingy, given that they use very little power.
I also have Raspberry Pi4 (8GB) that I run Ubuntu Desktop 20.04.4 on. I love it. It sits in my Living room on my coffee table. 

It also uses FrameBuffer for graphics. It doesn't do videos or streaming well at all, but I don't expect it to. For what it is and what i use it for, it does 'very' well. 

Other ARM devices... It all depends. A lot of ARM devices are supported, maybe in a round about way, but can work.

---

### Post by him610 on 2022-03-07
> ...getting a higher spec Raspberry Pi for a reasonable price.
Yes, if you can find one at all. After reading your post #7 last night, I searched ***fruitlessly*** on the internet for a Raspberry Pi Model 4. I have two earlier  Raspberry Pi devices - a Model B revision 2 and a Model 3B. I have Raspberry Pi OS (formerly Rasbian OS) on both of them.
```
$ bin/run-id.sh


    .~~.   .~~.         ___                __                      ___  _ 
   '. \ ' ' / .'       / _ \___  ___ ___  / /  ___  ___ ___ _ __  / _ \(_)
    .~ .~~~..~.       / , _/ _ `(_-</ _ \/ _ \/ -_) __/ __/ // / / ___/ / 
   : .~.'~'.~. :     /_/|_|\_,_/___/ .__/_.__/\__/_/ /_/  \_, / /_/  /_/  
  ~ (   ) (   ) ~                 /_/                    /___/          
 ( : '~'.~.'~' : )    
  ~ .~ (   ) ~. ~     Linux Version 5.10.92+
   (  : '~' :  )      Compiled #1514 Mon Jan 17 17:35:21 GMT 2022
    '~ .~~~. ~'       One 700MHz ARM ARM1176 Processor, 429M RAM
        '~'           698 Bogomips
                      rpiBr2
Startup finished in 6.995s (kernel) + 48.585s (userspace) = 55.581s 
graphical.target reached after 40.785s in userspace
Mon 07 Mar 2022 08:21:35 PM EST
                        ######           #####
 #####   #####      #   #     #  #####  #     #
 #    #  #    #     #   #     #  #    #       #
 #    #  #    #     #   ######   #    #  #####
 #####   #####      #   #     #  #####  #
 #   #   #          #   #     #  #   #  #
 #    #  #          #   ######   #    # #######

```
```
$ bin/run-id.sh
        _,met$$$$$gg.                                                           
     ,g$$$$$$$$$$$$$$$P.                                                        
   ,g$$P""       """Y$$.".                                                      
  ,$$P'              `$$$.                                                      
',$$P       ,ggs.     `$$b:                                                     
`d$$'     ,$P"'   .    $$$                               ,#.                    
 $$P      d$'     ,    $$P      ##:          :##        :###:                   
 $$:      $$.   -    ,d$$'      ##'          `##         `#'                    
 $$;      Y$b._   _,d$P'    __  ##     __     ##  __      _     __          _   
 Y$$.    `.`"Y$$$$P"'     ,####:##  ,######.  ##.#####. :### ,######. ###.####: 
 `$$b      "-.__         ,##' `###  ##:  :##  ###' `###  ##' #:   `## `###' `##:
  `Y$$b                  ##    `##  ##    ##  ##'   `##  ##    ___,##  ##:   `##
   `Y$$.                 ##     ##  #######:  ##     ##  ##  .#######  ##'    ##
     `$$b.               ##     ##  ##'       ##     ##  ##  ##'  `##  ##     ##
       `Y$$b.            ##.   ,##  ##        ##    ,##  ##  ##    ##  ##     ##
         `"Y$b._         :#:._,###  ##:__,##  ##:__,##' ,##. ##.__:##. ##     ##
             `""""       `:#### ###  ######'  `######'  #### `#####"## ##     ##

  Linux Version 5.10.92-v8+, Compiled #1514 SMP PREEMPT Mon Jan 17 17:39:38 GM
         Four 1.2GHz ARM Cortex-A53 Processors, 909M RAM, 154 Bogomips
                                     rpi3B

Startup finished in 4.195s (kernel) + 19.462s (userspace) = 23.658s 
graphical.target reached after 19.379s in userspace
Mon 07 Mar 2022 08:22:01 PM EST
                         #####  ######
 #####   #####      #   #     # #     #
 #    #  #    #     #         # #     #
 #    #  #    #     #    #####  ######
 #####   #####      #         # #     #
 #   #   #          #   #     # #     #
 #    #  #          #    #####  ######
 
```

---

### Post by MAFoElffen on 2022-03-08
I had bought a Starter Kit here: [https://www.canakit.com/raspberry-pi-4-8gb.html](https://www.canakit.com/raspberry-pi-4-8gb.html)
```

mafoelffen@ubuntu:~$ awk '/Model/ || /Revision/ {print $0}' /proc/cpuinfo
Revision    : d03114
Model        : Raspberry Pi 4 Model B Rev 1.4

mafoelffen@ubuntu:~$ lsb_release -sd
Ubuntu 20.04.4 LTS

```

---

### Post by ActionParsnip on 2022-03-08
I suggest a light desktop like LXDE to give more resources to your applications. You can install it via SSH. The default DM is fine (when asked). You can do this with
```

sudo apt udpate
sudo apt -y install lxde

```
Reboot and you will see a login page on the local display. You now have a desktop OS

---

