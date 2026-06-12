---
title: "Natty: Torbutton &amp; FireFox 4.0.1"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-05-01
Crap...

Every time FireFox is upgraded I have to go through a cycle of Torbutton not being compatible. Will I have to load the proxy settings manually everytime now?

Does anyone have an idea when this will be resolved; or should I downgrade my browser, and if so; which version should I downgrade to?

I'm currently on Firefox 4.0.1



Thanks, Hannibal

---

### Post by Mick007 on 2011-05-01
I am working on the same problem right now. I am running Natty as well, trying to downgrade to FF 3.6 and have nothing but problems.

---

### Post by coljohnhannibalsmith on 2011-05-02
Thanks for the reply,

I'm just using the Tor-Browser bundle from the Tor-Project now.  It doesn't need installation, so I'll just use this for the time being.

The upgrade to Natty also removed Tork automatically.  I much prefer Tork to Vidalia, because it is 'much' more powerful.  Instead of just randomly switching relays, it also allows you to select 'which' country you want to 'be' from.  It also allows you to manually select your relays and their order, and many other features that Vidalia will 'never' offer.

Tork was such a good app!



Hannibal

---

### Post by JohnH on 2011-05-04
Hi there,

I've got Vidalia happily sitting with Tor loaded but I can't get Tor Button to work at all. I've downloaded the latest alpha (which worked with FF4.0) but everything is now locked out. 

I can't even get Tor Browser to run.....

Upgrades can be very frustrating sometimes...I'll just have to wait until things catch up I guess.

Regards
John

---

### Post by jusis on 2011-05-04
I just now installed the newest alpha version, and it seems to work in firefox 4.0.1

---

### Post by jusis on 2011-05-04
[https://www.torproject.org/dist/tor-0.2.2.25-alpha.tar.gz](https://www.torproject.org/dist/tor-0.2.2.25-alpha.tar.gz)

or click on "install alpha" here:

[https://www.torproject.org/torbutton/index.html.en](https://www.torproject.org/torbutton/index.html.en)


it is mentioned that the version is unstable, though, whatever that may turn out to imply..

---

### Post by coljohnhannibalsmith on 2011-05-07
Thanks for the reply, [jusis]("http://ubuntuforums.org/member.php?u=1214368")

The first link you provided downloaded TOR, 'not' TORBUTTON, so I tried the second link, which delivered what it promised.

TORButton Alpha installed just like you said it would and works correctly.

I then surfed to:

[https://check.torproject.org/](https://check.torproject.org/)

And verified that TOR is indeed working.

I also surfed to:

[http://www.google.com/](http://www.google.com/)

and was redirected to:

[http://www.google.cz/](http://www.google.cz/)

&#268;eská republika

It's always fun to watch that happening, when TOR's running...:lolflag:
 
BTW, I wonder if anyone will be continuing delevopment on ***TOR'K.'  ***It was a great app, and someone needs to adopt that mutt, or add those features to Vidalia.




Just my opinion

---

### Post by coljohnhannibalsmith on 2011-05-17
[COLOR=Blue]***It appears this problem is now solved!!!***[/COLOR]

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

### Post by Captain_Falafel on 2011-05-25
> **coljohnhannibalsmith said:**
> Thanks for the reply, [jusis]("http://ubuntuforums.org/member.php?u=1214368")

The first link you provided downloaded TOR, 'not' TORBUTTON, so I tried the second link, which delivered what it promised.

TORButton Alpha installed just like you said it would and works correctly.

I then surfed to:

[https://check.torproject.org/](https://check.torproject.org/)

And verified that TOR is indeed working.

I also surfed to:

[http://www.google.com/](http://www.google.com/)

and was redirected to:

[http://www.google.cz/](http://www.google.cz/)

&#268;eská republika

It's always fun to watch that happening, when TOR's running...:lolflag:
 
BTW, I wonder if anyone will be continuing delevopment on ***TOR'K.'  ***It was a great app, and someone needs to adopt that mutt, or add those features to Vidalia.




Just my opinion

This isn't working for me for some reason. I did exactly this. I have FF 4.0.1, torbutton 1.3.3-alpha installed. When I go to a webpage when it's enabled, I get this FF error page: "The proxy server is refusing connections. Firefox is configured to use a proxy server that is refusing connections."
what am I doing wrong?

---

### Post by pengper on 2011-05-26
Sames here!

---

### Post by log_rima on 2011-05-30
Same here!!!! (Running from IRAN)

P.S.: It works like a charm in windows 7, and also I have checked the settings; Just the same!!

---

### Post by SynonM on 2011-06-08
> **pengper said:**
> Sames here!

Check for add-ons that might interfere with Tor button.

---

### Post by SynonM on 2011-06-08
> **Captain_Falafel said:**
> This isn't working for me for some reason. I did exactly this. I have FF 4.0.1, torbutton 1.3.3-alpha installed. When I go to a webpage when it's enabled, I get this FF error page: "The proxy server is refusing connections. Firefox is configured to use a proxy server that is refusing connections."
what am I doing wrong?


This is what I did...

stop all things related to Tor (or log off and log back in)

start terminal

```
sudo apt-get install aptitude
``````
 sudo aptitude reinstall tor tor-geoipdb polipo vidalia -y
```go here and skip to step four (4) do steps 4-6

[http://kyleabaker.com/2011/01/11/how-to-setup-and-use-tor-anonymity-in-ubuntu/](http://kyleabaker.com/2011/01/11/how-to-setup-and-use-tor-anonymity-in-ubuntu/)

and do this (quoted from [http://goshawknest.wordpress.com/2011/05/08/how-to-install-tor-on-ubuntu-natty-11-04/](http://goshawknest.wordpress.com/2011/05/08/how-to-install-tor-on-ubuntu-natty-11-04/)) 
(note: it is optional)
So it&#8217;s just uncommenting the two lines. **Tor** should be already working without any trouble, but it may be slow and u are not contributing to the **Tor** network. I highly suggest u to configure tor such that u can share your bandwidth with the network.
For changing this u have to modify */etc/tor/torrc *and change these two lines:[INDENT] #ORPort 9001
#DirPort 9030 
[/INDENT]into[INDENT] ORPort 9001
DirPort 9030 
[/INDENT]most importantly...

a program called Privoxy is known to interfere with Polipo
(I think it comes with a version of the Tor pkg but I don't know)

go to your terminal
```
sudo /etc/init.d/privoxy stop
``````
sudo /etc/init.d/polipo start
```next if you have not already goto  [https://www.torproject.org/torbutton/ ]("https://www.torproject.org/torbutton/")
then download the version of torbutton for your version of firefox (alpha = ff 4.0.1)
(stable = ff 3.)
start Vidalia
success = green onion 
start firefox 
Check for and then disable add-ons that might interfere with Tor button.
start or enable torbutton 


goto [https://check.torproject.org/](https://check.torproject.org/)
and if you don't get this
[IMG]http://img155.imageshack.us/img155/4228/minionion.png[/IMG]

I messed up or you did... ;) ... let me know.

---

### Post by abdulrahman alhussni on 2011-07-08
hello .... I did All that ... it worked for sometime ... but after restarting the computer vidalia refused to start tor because it was already running ... I solved this problem too after hundreds of Failed attempts ... But right now I have a new problem which i dont know its source which is this error message :

[Warning] The https proxy sent back an unexpected status code 403 ("Forbidden"). Closing.


I appreciate any help :)

---

### Post by SynonM on 2011-07-22
> **abdulrahman alhussni said:**
> hello .... I did All that ... it worked for sometime ... but after restarting the computer vidalia refused to start tor because it was already running ... I solved this problem too after hundreds of Failed attempts ... But right now I have a new problem which i dont know its source which is this error message :

[Warning] The https proxy sent back an unexpected status code 403 ("Forbidden"). Closing.


I appreciate any help :)


The best I can tell you is that you may have some other type of proxy device or software interfering. You might need to reinstall firefox and everything else of reinstall them.

use ```
sudo aptitude reinstall "name_of_software"
```
example ```
sudo aptitude reinstall firefox
```
or sudo apt-get remove "software"
then sudo apt-get install "software

---

### Post by SynonM on 2011-07-23
sorry it took so long to reply, but I think you might still be having trouble with privoxy. So run this before starting vidalia...

sudo /etc/init.d/privoxy stop

---

