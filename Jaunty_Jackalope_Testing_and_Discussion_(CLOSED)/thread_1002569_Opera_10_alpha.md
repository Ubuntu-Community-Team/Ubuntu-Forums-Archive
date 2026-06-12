---
title: "Opera 10 alpha"
date: 2008-12-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-12-05
Opera 10 alpha is out , get it here .):P
```
http://my.opera.com/desktopteam/blog/
```
NOTE! since it cannot be down graded back to earlier versions do not install it over your current opera . get the bz2 version not the .deb and unzip it into ~/home and run it from there with ./opera  that way it will run completely in its own dir and won't mess with your current version .

---

### Post by DougieFresh4U on 2008-12-05
How do I tell which version I need.
This would be for an Intel machine, which I see then theres the gcc3, gcc4, and then the qt3, qt4. I am kinda lost on that.
Thanks

---

### Post by plun on 2008-12-05
> **DougieFresh4U said:**
> How do I tell which version I need.
This would be for an Intel machine, which I see then theres the gcc3, gcc4, and then the qt3, qt4. I am kinda lost on that.
Thanks

Also add me to the lost ones...:D

"shared, bundled, static"

---

### Post by ronacc on 2008-12-05
sorry it took awhile to get back , I was away from the box for awhile . I am 64bit , the version I installed was . Opera-10.00-4103.gcc4-shared-qt3.x86_64.tar.bz2 .  the ones in the intel-linux dir would be for either amd or intel 32bit cpu's and also intel or amd 64bit cpu's in ubuntu 32 bit . the ones in the x86_64 dir would be for intel or amd 64bit cpus in 64bit ubuntu. I'm not sure what the gcc3/4 refers to gcc4 was the only choice under 64bit and it runs ok on my box , it probably refers to the version of gcc you have installed . The qt part does refer to the version of qt that you have , what the shared/static refers to is libqt-mt installed , that is for the shared version  the static version will run with or without that , that is the safest one to choose there .
as I said above get the tar version not the "bundled" and just extract it , installing the bundled version  with gdebi or dpkg would overwrite your existing Opera and you would NOT be able to revert . Opera will run fine without being installed and that way you can have both your current version and Opera 10 .

---

### Post by plun on 2008-12-05
OK... thanks. (I installed the deb version, ver 9 not installed)  

Starts like a rocket...:D everything also works for me, also sites filled with more "advanced" material.  

Nice !  (but its from Norway :D)

---

### Post by bpl07 on 2008-12-05
It seems java on amd64 is still not working in opera 10 alpha.  Someone correct me if I'm wrong.  It's unfortunate that it can't use the Icedtea plugin like firefox does.

---

### Post by ronacc on 2008-12-05
Java is working on my box , in Opera go to tools>preferences>advanced>content and make sure that enable java is checked then in java options see where your java path is pointed and validate it . mine points at  /usr/lib64/jvm/java-6-sun/jre/lib/amd64  .

---

### Post by ronacc on 2008-12-05
@ plun  write one in sweden and I'll test it :lolflag:

---

### Post by plun on 2008-12-05
> **ronacc said:**
> @ plun  write one in sweden and I'll test it :lolflag:

Well... Sweden and Norway has a special relationship....:D

We are neighbors and "just love" each other....  and now Norway got OIL.

Norway can buy whatever they wants....
[SIZE="1"]
but they also loves Microsoft[/SIZE]

EDIT forgot... but they are hacking a really good browser....   thumbs up !

;)

---

### Post by ronacc on 2008-12-05
yes but YOU hand out the Nobel prises;)

---

### Post by coolbrook on 2008-12-06
Decent speed improvement.

---

### Post by plun on 2009-01-23
@ronacc or another 64 bits freak....  ?

[http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/2008/de/tdtncmv.flv&title=The+Day+That+Never+Comes&desc=D](http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/2008/de/tdtncmv.flv&title=The+Day+That+Never+Comes&desc=D)


Only works for me with Opera.... the fox is out of order....;)

---

### Post by Slug71 on 2009-01-23
Just tried the link with FF and get;

Stream not found:tdtncmv.flv

---

### Post by plun on 2009-01-23
> **Slug71 said:**
> Just tried the link with FF and get;

Stream not found:tdtncmv.flv

Seems to be the same with this....

[http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/promo_vids/whiskey_in_the_jar_euro.flv&title=Whiskey+in+the+Jar+%28Uncensored+Version%29&desc=Director%3A+Jonas+Akerlund+%2D+Filmed+in+November+1998+in+Brooklyn%2C+NY+%2D+Video+Premiere+Date%3A+March+16%2C+1999+%2D+Mature+Audiences+Suggested](http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/promo_vids/whiskey_in_the_jar_euro.flv&title=Whiskey+in+the+Jar+%28Uncensored+Version%29&desc=Director%3A+Jonas+Akerlund+%2D+Filmed+in+November+1998+in+Brooklyn%2C+NY+%2D+Video+Premiere+Date%3A+March+16%2C+1999+%2D+Mature+Audiences+Suggested)

Opera OK...

---

### Post by gspat on 2009-01-23
They both work fine in FF for me???

Definately have to watch the second one later... :P

---

### Post by ronacc on 2009-01-23
both play fine for me in Opera 10 , FF3.05 ,FF3.1 on 64bit jaunty with flash 10 . couldn't try FF3.2 its crashing on startup right now .

---

### Post by xebian on 2009-01-23
No problem here too, even konqueror and minefield.

---

### Post by Slug71 on 2009-01-23
> **plun said:**
> Seems to be the same with this....

[http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/promo_vids/whiskey_in_the_jar_euro.flv&title=Whiskey+in+the+Jar+%28Uncensored+Version%29&desc=Director%3A+Jonas+Akerlund+%2D+Filmed+in+November+1998+in+Brooklyn%2C+NY+%2D+Video+Premiere+Date%3A+March+16%2C+1999+%2D+Mature+Audiences+Suggested](http://www.metallica.com/videoplayer/mediaplayer.asp?Media_Type=FLV&url=rtmp://cp57092.edgefcs.net/ondemand/flvstreams/metallica_com/promo_vids/whiskey_in_the_jar_euro.flv&title=Whiskey+in+the+Jar+%28Uncensored+Version%29&desc=Director%3A+Jonas+Akerlund+%2D+Filmed+in+November+1998+in+Brooklyn%2C+NY+%2D+Video+Premiere+Date%3A+March+16%2C+1999+%2D+Mature+Audiences+Suggested)

Opera OK...

Yep fails for me too. :confused:

---

### Post by ronacc on 2009-01-23
well now the question becomes, whats the difference between our installs ?

---

### Post by plun on 2009-01-24
> **ronacc said:**
> well now the question becomes, whats the difference between our installs ?

- Sound card must differs

- What flash version do you use ?   Ubuntus or  Adobes new 64 bits ?

---

### Post by gspat on 2009-01-24
I'm using Intel 82801BA-ICH2 for sound with latest nonfree plugin.

---

### Post by ronacc on 2009-01-24
adobes 64bit version ,hand installed, sound is nvidia on mobo no extra sound card .

---

### Post by plun on 2009-01-24
> **ronacc said:**
> adobes 64bit version ,hand installed, sound is nvidia on mobo no extra sound card .

Thanks and it works....

Just put libflashplayer.so within .mozilla/plugins


> You have version 10,0,21,1 installed

---

### Post by Slug71 on 2009-01-24
I have Ubuntu's flashplugin-nonfree(10.0.15) and Intel HDA onboard sound.

---

### Post by plun on 2009-01-24
> **Slug71 said:**
> I have Ubuntu's flashplugin-nonfree(10.0.15) and Intel HDA onboard sound.

I uninstalled Ubuntus flash and got the version from Adobe labs.

No meaning to file a bug either....  its a alpha or crap.....;)

---

### Post by Slug71 on 2009-01-24
> **plun said:**
> I uninstalled Ubuntus flash and got the version from Adobe labs.

No meaning to file a bug either....  its a alpha or crap.....;)

I will do the same.
I keep getting npviewer.bin crashes with this flash any way. nspluginwrapper is a piece of crap.

---

### Post by sirdilznik on 2009-01-24
I have to say I'm really impressed with the speed of this bad boy so far.  Of course I'm not using this in Jaunty, I'm using it in Intrepid, but that shouldn't make much difference.  Then again Opera has always been pretty fast (though maybe not this fast) for me, it was consistency and the occasional weird glitches on certain (very few) sites that kept me from switching from FF in the past.  I have my fingers crossed that they've worked those kinks out because I'm really liking it so far.

---

### Post by plun on 2009-01-24
> **Slug71 said:**
> I will do the same.
I keep getting npviewer.bin crashes with this flash any way. nspluginwrapper is a piece of crap.

Yup.... uninstall it !

The most incredible solo in history....

[http://youtube.com/watch?v=lWp-Mazmf88&feature=related](http://youtube.com/watch?v=lWp-Mazmf88&feature=related)

---

### Post by Slug71 on 2009-01-25
Yep works good now. :D

---

### Post by ubu-for on 2009-03-09
Opera doesn't offer Jaunty (i386) versions, so can someone please tell me which version could work.

opera-static_10.00.4102.gcc4.qt3_i386.deb
opera_10.00.4102.gcc3.qt3_i386.deb
opera_10.00.4102.gcc4.qt3_i386.deb
opera_10.00.4102.gcc4.qt4_i386.deb

What is a static version?

Thanks in advance!

---

### Post by nyarnon on 2009-03-09
@ubu-for
Go and read the first message again.

---

### Post by ubu-for on 2009-03-09
> **nyarnon said:**
> @ubu-for
Go and read the first message again.

You think of the note "do not install the deb packages"? :mrgreen:

I don't have Opera installed yet!

---

### Post by nyarnon on 2009-03-09
That doesn't matter read on, posting 4 gives you more clues.

---

### Post by ubu-for on 2009-03-09
> **nyarnon said:**
> That doesn't matter read on, posting 4 gives you more clues.

I've read it hours ago and was still unsure. That's why I had that question.

I think I have gcc 4 but I don't know, if I have qt3 or qt4 because my Synaptic is broke. Maybe there is a command to find out the correct version but I'm not a Linux pro.

---

### Post by ronacc on 2009-03-09
use this one opera_10.00.4102.gcc4.qt3_i386.deb  , that is of course you are 32bit , if you are 64bit use the amd64 same version . BTW the current build is 4116 not 4102 . so use opera_10.00.4116.gcc4.qt3_i386.deb  .

---

### Post by ubu-for on 2009-03-09
> **ronacc said:**
> use this one opera_10.00.4102.gcc4.qt3_i386.deb  , that is of course you are 32bit , if you are 64bit use the amd64 same version . BTW the current build is 4116 not 4102 . so use opera_10.00.4116.gcc4.qt3_i386.deb  .

Thanks!

Do you have a link to the file because I only get the 4102 version, if I click on [10.0 Alpha 1](http://snapshot.opera.com/unix/).

---

### Post by vredley on 2009-03-09
It's the 'Valentine's snapshot':

[http://snapshot.opera.com/unix/snapshot-4166/intel-linux/](http://snapshot.opera.com/unix/snapshot-4166/intel-linux/)

---

### Post by ronacc on 2009-03-09
you can always find the latest snapshot here . [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)    .

---

### Post by plun on 2009-03-13
> **ronacc said:**
> you can always find the latest snapshot here . [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)    .

[http://labs.opera.com/news/2009/03/13/](http://labs.opera.com/news/2009/03/13/)

with turbo....:D

---

### Post by ronacc on 2009-03-13
thanks for the heads up , got it d/l'ing now .

---

### Post by ubu-for on 2009-03-14
> **vredley said:**
> It's the 'Valentine's snapshot':

[http://snapshot.opera.com/unix/snapshot-4166/intel-linux/](http://snapshot.opera.com/unix/snapshot-4166/intel-linux/)

> **ronacc said:**
> you can always find the latest snapshot here . [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)    .

Thanks for your help!

---

### Post by agitdd99 on 2009-03-19
i'm downloading build 4205 now [http://snapshot.opera.com/unix/snapshot-4205/intel-linux/](http://snapshot.opera.com/unix/snapshot-4205/intel-linux/)
but i look again some of your post guys, and  i find the latest opera 10 version with turbo: [http://snapshot.opera.com/unix/10-turbo/intel-linux/](http://snapshot.opera.com/unix/10-turbo/intel-linux/)

update:
i installed a few hours ago...and i think it's better than the previous version. i've tested it with acid3 and resulting at score 99/100.
but here is some differences with FF 3.0.7, and might be it's still need improvements.

[IMG]http://farm4.static.flickr.com/3418/3367727352_fbb9ecd82b_b.jpg[/IMG]

---

### Post by Colonel Kilkenny on 2009-03-19
> **agitdd99 said:**
> 
but here is some differences with FF 3.0.7, and might be it's still need improvements.


Only difference I can see is that you're using Opera Turbo and that's why the image is compressed. IMHO there's no need for Turbo unless you're using internet through mobile or otherwise slow network.

And Opera 10 with Turbo is Opera Labs release so it is released just to show the Turbo feature on desktop.

---

