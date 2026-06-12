---
title: "Setting up a rock solid Ubuntu Desktop with SSD and  components suggestion"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by SayakBiswas on 2015-02-15
Dear All,


This is my first ever post on Ubuntu-forums, so please bear with me. 
I apologize in advance for my English, as it is not my native language.

After tinkering around with Ubuntu on my laptop for the last year, I have decided to finally jump the boat and use Ubuntu 14.04 LTS on my gaming desktop as the primary OS. I have just bought my first ever SSD (Toshiba SSD Q Series Pro 128Gb), and I am going to use it exclusively for Ubuntu. My current HDD is an old(~2008) Seagate Barracuda 360GB ,7200rpm drive. My gaming desktop(already three years old) will become my family's primary computer, and I want it to last for at least the next 5-7 years. From now on its primary use will be net surfing,youtube, HD movie playback, occasional word-excel-powepoint, skype, photo/image editing, occasional games like counter strike, dota2 and 0AD. The software used will mainly be : Chrome,Firefox,Skype,VLC,Audacious,Libreoffice,Darktable,GIMP,Steam, Eset NOD32 Antivirus, Tixati,Spotify,Team Viewer. 

My queries are as follows:

1) What I am confused about is how to set up my "home" folder. I was thinking about setting up the main OS on the SSD with my "home" folder on the HDD. If i do so, will the HDD hamper the speed of the SSD??? And should I use a swap file on the SSD or HDD or go without one altogether???

2) Also, does anyone have any experience using this particular SSD with linux........is it any good??? I bought it because I trust Toshiba more than Kingston/Sandisk/Transcend and the similarly priced Samsung 840 EVO has a read speed problem. The Toshiba is reviewed well on the internet, but they all tested it on Windows.This is my first ever SSD, so I am a bit nervous.

3) Does the SATA cable matter a lot for the SSD??? I have ordered this one : "BitFenix Alchemy SATA 6 GB/s 30 cm Braided Cable".        Link :-  [http://www.snapdeal.com/product/bitfenix-alchemy-sata-6-gbs/650534412](http://www.snapdeal.com/product/bitfenix-alchemy-sata-6-gbs/650534412)

4) One of my biggest concerns is that since my desktop wont have windows any more, how do i upgrade firmware/BIOS for SSD/Motherboard etc.?

5) Is there a way to install the game 0AD in a folder of my choice on the HDD and not the SSD???

6) Also could someone recommend the following components with good linux driver support - a) usb wifi dongle     b) usb bluetooth dongle        c) Internal sound card
 
7) I want your opinions on whether my desktop is powerful enough for its intended future. If not, which parts should i upgrade???My config is as follows:

                    AMD Phenom II 965 (no overclock)
                    Cooler Master Hyper TX3 EVO cooler
                    ASUS M5A97 LE R2.0 motherboard (this is the second mbd, first one was a Gigabyte, it died after 2.5 years)
                    Corsair Vengence 8GB (2x 4GB) DDR3 1600 Mhz RAM( I might add another 2x4GB sticks later)
                    Powercolor Radeon HD 6950 2GB DDR5 GPU
                    Toshiba SSD Q Series Pro 128Gb (not yet installed as i am still waiting for the SATA cable........the wait is unbearable......I want to experience an SSD!!!!!!)
                    Seagate Barracuda ST3360320AS 360GB HDD
                    Corsair CX600 PSU
                    Dell ST2220L HD LED Monitor 
                    TVS Mechanical Keyboard
                    Logitech M905 wireless Mouse
                    Logitech c525 webcam
                    Apc 700va ups


For reference :- My CPU temp is 38-46 C for normal use and 55-58 C while running Handbrake for a few hours. My GPU temp is 39-48 C at desktop and 75-80 C in full load. Motherboard temp is 31-34 C and HDD temp is 33-37 C. I will be using proprietary Radeon drivers.

I eagerly await everyone's opinions, and thank you all for the patience to go through my post and bear with my english :)




Sincerely,

Sayak.

---

### Post by v3.xx on 2015-02-15
If I had a SSD (I don't) I put everything on it that could fit.  I would want the whole system and home on it.  [But I use ram instead.]("http://ubuntuforums.org/showthread.php?t=1594694")

---

### Post by kerry_s on 2015-02-15
1. home on ssd. you have 8gb ram you can skip having a swap. just format the drive as ext4 & select /
use the hdd for storage/saving things.

2. no
3. i don't think so
4. most boards are updated by boot disk/usb
5. no, cause it's installed via apt-get
6. look for ralink wifi, don't know, don't know
7. i would say it's already more power than you need. :)

---

### Post by SayakBiswas on 2015-02-15
To v3.xx 


Thank you, that ram booster stuff is really interesting, will try it out tomorrow.


Regards,
Sayak.

---

### Post by SayakBiswas on 2015-02-15
> **kerry_s said:**
> 1. home on ssd. you have 8gb ram you can skip having a swap. just format the drive as ext4 & select /
use the hdd for storage/saving things.

2. no
3. i don't think so
4. most boards are updated by boot disk/usb
5. no, cause it's installed via apt-get
6. look for ralink wifi, don't know, don't know
7. i would say it's already more power than you need. :)




Thank you for the quick reply.


Regards,
Sayak.

---

### Post by SayakBiswas on 2015-02-18
Installed my SSD, fully loaded and heavily customised system now boots under 25 seconds. Applications load in a snap.

Benchmark Results are as follows:

TOSHIBA Q Series Pro 128GB SSD.
Ubuntu 14.04 (kernel 3.13.0-46)

Read speed - 531 MB/s
Write speed - 492 MB/s


Its a little slower than the advertised speeds of 554/512, but i am still very happy with it.

I used the following SSD optimisation tips from the following link : [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

