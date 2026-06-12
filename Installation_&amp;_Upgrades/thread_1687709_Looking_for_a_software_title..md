---
title: "Looking for a software title."
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by KajiMaster on 2011-02-14
I picked the best forum section for my inquiry but not sure it's totally applicable.  Please move if there is a section more suitable. 

I have recently been discovering the amazing benefits that my LAMP server can provide me.  I have used Jenzora to organise my MP3 collection via a website that I can access from any browser in the world.  I also recently set up TorrentFlux so i could remotely manage torrent downloads on my server via a browser.  This is great for breaks at work.  I can do things I normally wouldn't be able to do due to the proxy blocking my access to various sites.  Now on to my question.

There has got to be some software that will allow me to browse full graphic websites via a web site.  Yeah I know that probably doesn't make sense but let me explain.  My server is at home connected to my cable Internet.  I have full access to the whole web.  But at work lots of things are blocked.  There has got to be a way I could via a web browser connect to my server and browse web pages via the connection on the server.  I would almost call it a web based web browser.  I have tried googleing this every way possible and can't find anything.  There must be a technical term for this but I can't pin point it. 

I know there where some websites out there specificity designed for you go around the proxy, i think this is what I'm looking for.  Anyone know any programs by title that would do this for me?  I'm not looking to just SSH into my box and use lynx to browse text based... I need the full graphical usage. 

Thanks much,
Kaji

---

### Post by cjhabs on 2011-02-14
If you have an Xserver on your machine at work, you can simply ssh with -X switch to your home machine and fire up Firefox (or any graphical app) and it will display back to your local X server at work.

---

### Post by KajiMaster on 2011-02-14
My box at home is Ubuntu Server, no GUI.  Also I would like to have it via web address so my girlfriend can get on netflix during her lunch break... having her ssh -x etc would be way to much for her

---

### Post by KajiMaster on 2011-02-14
Solved my own problem.  The program I was looking for was Glype.  However, I would like soemthing a little bit more advance... I still can't get on netflix and browse moves... i can see the main site and other websites.

---

