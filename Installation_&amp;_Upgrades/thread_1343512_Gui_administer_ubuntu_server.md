---
title: "Gui administer ubuntu server"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by makoshark55 on 2009-12-01
Hello and Merry Christmas
I have been working on setting up ubuntu server on a local net work to run my Zen-cart shopping cart software. In my search I have come across a lot of rants about putting a GUI on the server. This is not much help to me. I am disabled and having a desktop is important. Also I know nothing about running a server I am trying to learn. I have added ```
sudo apt-get install ubuntu-desktop                      
``` but it seems like a lot of program for what I want to do. I guess what I am realy after is so kind of way to administer the LAMP from the screen and not command lines. I found something about ebox but I am not sure how to install and use it.
Thanks James

---

### Post by Aearenda on 2009-12-02
Ebox is a sort of pre-cooked system where the admin UI and the packages installed are managed all together. It has a web UI and is good at making sure everything is 'just so', according to the Ebox developers' view; but you have to do everything the Ebox way. It's admin UI is a little slow at times, but very thorough.

An alternative is Webmin, which has a web UI with a lot of add-ons to manage all sorts of things. Webmin doesn't try to force you to use particular packages, and doesn't get upset if you modify configs behind its back. Webmin is not favoured by the Ubuntu server developers, but I find it quite acceptable, and it is widely used. See [http://www.webmin.com/](http://www.webmin.com/), and be aware that there are no webmin packages in the Ubuntu repository so you have to install it from their site.

---

### Post by phillw on 2009-12-02
> **Aearenda said:**
> Ebox is a sort of pre-cooked system where the admin UI and the packages installed are managed all together. It has a web UI and is good at making sure everything is 'just so', according to the Ebox developers' view; but you have to do everything the Ebox way. It's admin UI is a little slow at times, but very thorough.

An alternative is Webmin, which has a web UI with a lot of add-ons to manage all sorts of things. Webmin doesn't try to force you to use particular packages, and doesn't get upset if you modify configs behind its back. Webmin is not favoured by the Ubuntu server developers, but I find it quite acceptable, and it is widely used. See [http://www.webmin.com/](http://www.webmin.com/), and be aware that there are no webmin packages in the Ubuntu repository so you have to install it from their site.

+1 for Webmin

And +1 that it is a shame it is not in the repositry.

Phill.

---

### Post by makoshark55 on 2009-12-03
Ok what do I do with Webmin? does it go on client ubuntu 9.10 or the ubuntu server. I only have command line at the server. I am looking for a small graphic program to administer my ubuntu server

---

### Post by makoshark55 on 2009-12-06
Well I broke down and put the ubuntu desktop on the server. This is no so bad as I was able to get webmin to work on my server. I was a little work to get webmin configured to run, but it is fine now. My server is going to have a copy of [http://shop.nilandsplace.com/camp/index.php](http://shop.nilandsplace.com/camp/index.php). This is so I can experiment with Zen Cart and not break my live shop. I can access webmin remotely but I have not figuered out how to set up my zen cart. Do I have to set up a public directory (folder for you youngsters) and how do I go about it with webmin? Is it over my head to set up a web-host? Hey this posting came up third in google so think about what you want to say.

---

