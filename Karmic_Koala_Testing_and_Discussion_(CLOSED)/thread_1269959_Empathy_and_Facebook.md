---
title: "Empathy and Facebook"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-09-18
Does anyone have a working Facebook connector with Empathy?  I have tried lots of threads and nothing has worked.  I noticed my server field isnt filled in.  Anyone?

---

### Post by zorkerz on 2009-09-25
By "connector" do you mean something that allows you to use facebook chat in empathy?

Previously I was able to do this using the directions found here [http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/](http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/)
actually quoting from another ubuntu forums post. 

More recently this has stopped working for me. I would like to be able to use facebook chat in empathy. This is a bit of a deal breaker for me.

---

### Post by knahrvorn on 2009-10-13
> **zoomy942 said:**
> I noticed my server field isnt filled in.  Anyone?

I'm having this problem, too. I followed the guide at [http://ubuntuforums.org/showthread.php?t=973830](http://ubuntuforums.org/showthread.php?t=973830) (message #8), only not the last part.

I am now able to select facebook as a new account, but after typing in my facebook account details and clicking "Connect", nothing happens. Probably because, under "Advanced", the "Server" setting is blank. Does anyone know which server to use?

Thanks in advance!

---

### Post by hanzomon4 on 2009-10-13
Grab the plugin from the project site. Then sudo rm /usr/share/telepathy/managers/haze.manager. After that restart empathy and put in your info for facebook. It won't connect, but try restarting. That worked for me.

---

### Post by knahrvorn on 2009-10-16
> **hanzomon4 said:**
> Grab the plugin from the project site. Then sudo rm /usr/share/telepathy/managers/haze.manager. After that restart empathy and put in your info for facebook. It won't connect, but try restarting. That worked for me.

Thanks! Following the guide at the bottom of [http://live.gnome.org/Empathy/Protocols](http://live.gnome.org/Empathy/Protocols) (and then restarting), did it for me, too.

---

### Post by yosemite610 on 2009-10-16
> **knahrvorn said:**
> Thanks! Following the guide at the bottom of [http://live.gnome.org/Empathy/Protocols](http://live.gnome.org/Empathy/Protocols) (and then restarting), did it for me, too.

Ditto to those instructions, Empathy 'sees' Facebook chat now...

---

### Post by davidmohammed on 2009-10-16
... didnt work for me - pressing connect doesnt do anything.  Restarting doesnt have the facebook account I created.  Any ideas?

---

