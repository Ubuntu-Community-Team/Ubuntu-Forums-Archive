---
title: "OpenOffice fonts ugly after upgrading to Edgy Eft"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by zilverling on 2006-10-27
Font rendering in OpenOffice menus but also in the docs themselves has become very ugly after upgrading to Edgy Eft.:evil: there is [a thread on this]("http://ubuntuforums.org/showthread.php?p=1587443"), but no solution so far... I'm almost considering to move back to Dapper (if possible).](*,)

---

### Post by Judicata on 2006-10-27
I can confirm this.  I've also been surfing the bug reports, etc... and there seems to be no solution for this so far.  As you can see from the screenshot, Word looks its usual "ok," Abiword looks great, and OO.o looks...a little yucky (could be worse, though).

---

### Post by cptjaben on 2006-10-27
I seem to be having the same problem in firefox, possibly in openoffice though I haven't checked yet.

---

### Post by rubinstein on 2006-10-28
There is no (easy) solution to this font problems for OpenOffice.org. (The only working solution is to copy your openoffice directory and also libfreetype library from dapper to edgy).

My solution was to stick with dapper. Plain and simple.

---

### Post by cptjaben on 2006-10-28
I was able to fix my font problem by enabling subpixel smoothing and subpixel Hinting.

---

### Post by nbx909 on 2006-10-28
what exact ones would i need to copy?

---

### Post by rubinstein on 2006-10-29
> **nbx909 said:**
> what exact ones would i need to copy?

Look at [http://www.ubuntuforums.org/showthread.php?t=272470&page=6](http://www.ubuntuforums.org/showthread.php?t=272470&page=6) for the exact procedure by schrodycat.

---

### Post by martijndenerd on 2006-10-29
> **cptjaben said:**
> I was able to fix my font problem by enabling subpixel smoothing and subpixel Hinting.
Where do you do this? Because I already set it in the kde settings, is there another place to do this?

---

### Post by Rui Pais on 2006-10-29
> **martijndenerd said:**
> Where do you do this? Because I already set it in the kde settings, is there another place to do this?

some people seems to solve the problem, specially with FF fonts, with subpixel hiting, but for others it won't work :(
If you set it in kde settings you are probably in this last case. With me it make it a little better but not solve it either :(

---

### Post by NorQue on 2006-10-29
I'm having the same problem as Judicata, but additionally the menu fonts in OpenOffice look distorted, too - I've attached a Screenshot to show what I mean. OpenOffice is the only programm with this weird font behaviour for me.

I would be very happy if someone had a solution that doesn't involve re-installing Dapper or getting files from it, since I unfortunately don't have it around anymore.

Thanks in Advance,

-- NorQue

---

### Post by Athropos on 2006-10-30
> **NorQue said:**
> I'm having the same problem as Judicata, but additionally the menu fonts in OpenOffice look distorted, too

Hey, you're lucky :p
Fonts in OpenOffice on my system are far less readable...

---

### Post by jferrando on 2006-10-30
This second very annoying thing with openoffice has got me very upset.

First non-solved issue for me was the <B>unability to open and save files properly in cifs shares</B> (mounted):
mount -t cifs //surera.netplc.com/datos /home/jferrando/csurera -o credentials=/etc/smbc.jordi,uid=1000,gid=1000,iocharset=utf8

Of course, openoffice "official" response was "use a file-locking capable system, such as NFS"... And what else? I print my server's root password and post in on my web page? NFS is not secure.

Even this simple issue has me forced of using vmware'd Win2000 in my company network, I can't afford overriting files of other people in the server.

Now, even worse, these OpenOffice people **disable decent font rendering in the Openoffice "core"**... seems that micro$oft is paying them to keep us away from desktop Linux....

---

### Post by Footer on 2006-11-01
> **Rui Pais said:**
> some people seems to solve the problem, specially with FF fonts, with subpixel hiting, but for others it won't work :(
If you set it in kde settings you are probably in this last case. With me it make it a little better but not solve it either :(

I've tried this in the past (subpixel hinting, rendering, smoothing etc. via KDE) and while it improves some fonts on the system, it makes others worse.  It used to be so simple to fix the OO fonts (under Dapper and previous) but alas, that ability has been removed in Edgy.

It's enough to make you want to switch distros ...

](*,)

---

### Post by waldorf on 2006-11-07
Has anything new developed on this? Please someone help or fix this!

---

### Post by Rui Pais on 2006-11-07
maybe [give this]("http://ubuntuforums.org/showthread.php?p=1713034#post1713034") a try (not worked for me but, who knows...)

---

### Post by okl on 2006-11-07
> **waldorf said:**
> Has anything new developed on this? Please someone help or fix this!

There is an easy way to fix it:
1. Deinstall all openoffice packages from edgy
2. Get the 2.0.4 debian packages from [www.openoffice.org](www.openoffice.org)
3. tar xfz OO...
4. cd DEBS
5. dpkg --install *.deb
6. copy libfreetype.so.6.3.8 from dapper to /usr/local/lib/
7. export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
8. /opt/openoffice.org2.0/program/simpress

Now you have a 2.0.4 office with auto-hinting and very nice fonts!

okl

---

### Post by waldorf on 2006-11-07
Okay sounds like a plan - thanks!

but I don't quite follow:

3. tar xfz OO...
4. cd DEBS

can you be more specific (or explain this)?

and

6. copy libfreetype.so.6.3.8 from dapper to /usr/local/lib

On number 6 how do I get libfreetype.so.6.3.8 from dapper?

Thank you thank you

Waldorf

---

### Post by Rui Pais on 2006-11-07
> **waldorf said:**
> ...
On number 6 how do I get libfreetype.so.6.3.8 from dapper?

it's in /usr/lib/libfreetype.so.6.3.8 of a normal dapper installation.

If you dont' have Dapper installed or a dapper livecd you can get the deb [here]("http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb"), 
and open it with file-roller (it's inside data.tar.gz)

---

### Post by waldorf on 2006-11-07
> **Rui Pais said:**
> it's in /usr/lib/libfreetype.so.6.3.8 of a normal dapper installation.

If you dont' have Dapper installed or a dapper livecd you can get the deb [here]("http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb"), 
and open it with file-roller (it's inside data.tar.gz)
Great, Thanks!

Can anyone tell me what I do with:

3. tar xfz OO...
4. cd DEBS

---

### Post by okl on 2006-11-07
Hello waldorf,

load the debian file from [www.openoffice.org](www.openoffice.org)
For me (I use the german version) it will download a file called:
OOo_2.0.4_LinuxIntel_install_de_deb.tar.gz
Then open a terminal and type:
tar xfz OOo_2.0.4_LinuxIntel_install_de_deb.tar.gz
this will unpack the tar-archive to a directory called DEBS.
Change to this directory by typing "cd DEBS".
Then install the deb-Files in this directory by typing:
"sudo dpkg --install *.deb"
Now you can type 
"export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8"
And then start the program with
"/opt/openoffice.org2.0/program/simpress"

To avoid typing the export line every time starting openoffice you may want to change the file /opt/openoffice.org2.0/program/soffice with a text-editor and add the "export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8" as second line.
Now you can create a desktop-icon which points to /opt/openoffice.org2.0/program/soffice and there you go.
Sounds more complicated than it actually is.
I attach a screenshot of my openoffice.org-2.0.4 running on edgy.
okl

---

### Post by Rui Pais on 2006-11-07
> **okl said:**
> ...
And then start the program with
"/opt/openoffice.org2.0/program/simpress"
...
okl

sorry, but why simpress? shouldn't be soffice?

---

### Post by waldorf on 2006-11-07
> **okl said:**
> There is an easy way to fix it:
1. Deinstall all openoffice packages from edgy
2. Get the 2.0.4 debian packages from [www.openoffice.org](www.openoffice.org)
3. tar xfz OO...
4. cd DEBS
5. dpkg --install *.deb
6. copy libfreetype.so.6.3.8 from dapper to /usr/local/lib/
7. export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
8. /opt/openoffice.org2.0/program/simpress

Now you have a 2.0.4 office with auto-hinting and very nice fonts!

okl
I actually got hung up on the first step. When I use synaptic to remove all openoffice packages I get an error:

Could not apply changes!
Fix broken packages first.

Not sure what is up.

Thanks to Okl and Rui Pais

---

### Post by okl on 2006-11-07
> **Rui Pais said:**
> sorry, but why simpress? shouldn't be soffice?

It may also be soffice or scalc or swriter. whatever :-D
I worked the whole day for a presentation with impress. that's why I typed it here. 
okl

---

### Post by Rui Pais on 2006-11-07
> **waldorf said:**
> I actually got hung up on the first step. When I use synaptic to remove all openoffice packages I get an error:

Could not apply changes!
Fix broken packages first.

Not sure what is up.

Thanks to Okl and Rui Pais

You have broken packages on your system... :(

On synaptic click on 'Custom' button on left bottom and on the list (bellow All) you got an entry, 'Broken'. Click and you'll see what it's broken

[QUOTE=okl]It may also be soffice or scalc or swriter. whatever
I worked the whole day for a presentation with impress. that's why I typed it here.
okl[/QUOTE]

oh, i see. ok :)

---

### Post by waldorf on 2006-11-07
Okay got the broken packages addressed but I can't seem to find the deb of OO on the OO website. the link is for an rpm.

Thanks for holding my hand through this guys!

---

### Post by Rui Pais on 2006-11-07
> **waldorf said:**
> Okay got the broken packages addressed but I can't seem to find the deb of OO on the OO website. the link is for an rpm.

Thanks for holding my hand through this guys!

the main english version is [here]("http://download.openoffice.org/2.0.4/contribute.html?product=OpenOffice.org&os=linuxintel&lang=en&version=2.0.4").
Other languages can be chosen [here]("http://projects.openoffice.org/native-lang.html").

As far as i have read on the forums a lot of people solve this problem just by get a dapper version of libfreetype and launch OO with the LD_PRELOAD trick mentioned by okl. 
Maybe you should try that first to see if you can solve your problem easier.

good luck.

---

### Post by waldorf on 2006-11-07
> **Rui Pais said:**
> the main english version is [here]("http://download.openoffice.org/2.0.4/contribute.html?product=OpenOffice.org&os=linuxintel&lang=en&version=2.0.4").
Other languages can be chosen [here]("http://projects.openoffice.org/native-lang.html").

As far as i have read on the forums a lot of people solve this problem just by get a dapper version of libfreetype and launch OO with the LD_PRELOAD trick mentioned by okl. 
Maybe you should try that first to see if you can solve your problem easier.

good luck.
good idea!

how do I find the libfreetype on a 6.06 cd?

---

### Post by waldorf on 2006-11-08
> **waldorf said:**
> good idea!

how do I find the libfreetype on a 6.06 cd?
Well I tried the whole libfreetype thing (figured out how to get it) and it didn't work. Honestly I'm I bit discouraged and wonder why it takes all these steps to fix something that really should not be a problem in the first place. I love ubuntu and really appreciate all that everyone does to make it happen and really appreciate the community so please don't take this as an big criticism, but it does seem crazy that something so basic as fonts is off.

---

### Post by okl on 2006-11-08
> **waldorf said:**
> Well I tried the whole libfreetype thing (figured out how to get it) and it didn't work. Honestly I'm I bit discouraged and wonder why it takes all these steps to fix something that really should not be a problem in the first place. I love ubuntu and really appreciate all that everyone does to make it happen and really appreciate the community so please don't take this as an big criticism, but it does seem crazy that something so basic as fonts is off.

For me it was not enough to just use the libfreetype library from dapper with the edgy openoffice. I had to use either the openoffice packages from dapper (the 2.0.2 version) or the openoffice-packages from debian (2.0.4 version).
I can understand your comment as I have to work with openoffice every day and these ugly fonts are out of the question,
but no one has done this on purpose. The only problem I see is that there are people who believe that this is just a cosmetical problem but if you use impress for presentations and it has too many of these ugly problems than this will turn out to be a monetary problem. 
But there is no easy solution because openoffice 2.0.4 does not work properly with the new libfreetype but the complete edgy is linked against this new libfreetype and is working. So this problem cannot be solved by just recompiling new openoffice packages. It's a problem beyond the direct sphere of ubuntu. The only thing you may ask is whether it was a good idea to upgrade libfreetype from dapper to edgy while this major application ooo is not working properly with it.

If you have problems with getting deb-files for openoffice 2.0.4 you can just use the ones that come with dapper (2.0.2) and use the export LD_PRELOAD command. This will also work.
The only solution apart from that will be to wait for a fix in openoffice or freetype so the two will collaborate together again.

okl

---

### Post by Rui Pais on 2006-11-08
Well this is not an ubuntu problem. You can find threads like this  on gentoo or fedora forums, or more generically at ooffice forums.

It's a problem of incompatibilities on new versions of Freetype and how OO deals with font rendering and hinting (and how OO devs deal with changes on opensource/Linux software, know to be a little too... uhm... conservative :-k )

If you can't solve that issue in Edgy you can give Dapper a try. Don't forget that the both ubuntus are actual releases, dapper is a LST, and in many cases much more stable. If you want/need to use the 2.0.4 version instead of original dapper 2.0.3, use the OpenOffice's site version installed with the same procedure as the one suggested by okl. For me work perfectly.

---

### Post by waldorf on 2006-11-08
Thanks again guys for talking this through. I guess I'm wondering about this. I don't need to use OOo 2.0.4 and would be perfectly happy using 2.0.3 or 2.0.2. Maybe the best thing to do is to remove 2.0.4 and use an older version - yes/no? Perhaps that is a bigger headache. I don't know because I would not know how to do that.

Thoughts?

Thanks again!

---

### Post by okl on 2006-11-08
> **waldorf said:**
> Thanks again guys for talking this through. I guess I'm wondering about this. I don't need to use OOo 2.0.4 and would be perfectly happy using 2.0.3 or 2.0.2. Maybe the best thing to do is to remove 2.0.4 and use an older version - yes/no? Perhaps that is a bigger headache. I don't know because I would not know how to do that.

Thoughts?

Thanks again!

Hi,

you can go back to the 2.0.2 version. Therefor you first need to deinstall openoffice 2.0.4 completely. Then edit the sources.list file by typing
"sudo nano /etc/apt/sources.list" in the terminal.
Look for the line:
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
and change "edgy" to "dapper" then save the file and close the editor.
After that type "sudo apt-get update"
then start synaptic and install openoffice. This will install the dapper version of openoffice.
After the installation edit the sources.list file a second time and change "dapper" back to "edgy" like it was before.
Perhaps you may want to block the openoffice packages after that because synaptic will suggest to upgrade openoffice back to 2.0.4.
BUT you will still have to enter
export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8
ooffice
to start openoffice because also the dapper version of openoffice will not work with the new libfreetype so the export option ensures the use of the old version.

Otherwise it may be an option to backup all your personal data and install dapper. There Openoffice will be fully functional out of the box.

okl

---

### Post by waldorf on 2006-11-08
Okay, so it sounds like going back to 2.0.2 is really no better than sticking with 2.0.4 because there is still the libfreetype issue. Not sure what I'll do, but I may very well wait until OOo and freetype work it out between themselves and provide an update that fixes this.

How do I put in my two cents and let them know that IMHO it should be fixed?

Thanks again, Waldorf

---

### Post by Footer on 2006-11-08
Over the last 18 hours or so, I've been battling these OO ugly font issues in Edgy ... Actually, I've been battling it since I upgraded to Edgy but finally decided to try to resolve it.  Anyway, I just finished reinstalling Dapper and finally got my problems fixed.  I started a thread like this one over on the Kubuntu forums:

[http://kubuntuforums.net/forums/index.php?topic=10385.0](http://kubuntuforums.net/forums/index.php?topic=10385.0)

It kind of turned out to be a long thread. :)  But ultimately, going back to Dapper was the only acceptable solution for me.  When they get this OO/freetype thing sorted out, I may upgrade to Edgy again ... but ONLY if OO fonts are as good as or better than they are/were in Dapper!

---

### Post by fotakis on 2006-11-11
Bigup to okl, 

Thank you very much!!!!!!

You have saved me from many hours of agony


I have finally openoffice the way you have in your screen shoot!!

For anyone interested I can vouch for that the method  [#20]("http://ubuntuforums.org/showpost.php?p=1728301&postcount=20")
really works.

I am using edgy eft.

One caveat, I wasn't able to find any .deb packages. So I had to download the rpms from the link that okl provided.

After downloading 120Mb , I installed using alien

# cd *untarred directory/RPMS*
# sudo alien -i --scripts *.rpm


After a small wait done. Launched and woila!!!!

All I have to do is add the menu items with Alacarte

Once again, thank you to this great community, you have made my switch come true :-)!!!!

Edit::

From my exitement, i didn't look at things through, I don't think the alien installation set the mime-types for oo documents, and I can seem to find the icons anywhere under /opt/openoffice-2.0.4/

Could anybody provide any help on this? OKL?

Second Edit::

To answer my own question you can see [HERE]("http://www.reallylinux.com/docs/oo2install.shtml")

at the end of the articles he tells you how to achieve menu integrations

---

### Post by okl on 2006-11-13
> **fotakis said:**
> Bigup to okl, 

Thank you very much!!!!!!

You have saved me from many hours of agony


Hi fotakis,

:D That are good news. Sorry I couldn't check this thread the last days but as I see you have already found the "desktop-integration" directory.
Hopefully other people will also try this openoffice-version. It sounds more complicated than it  actually is! Would be a sad thing if many people reinstall dapper again just because of this bug. 

okl

---

### Post by Yv12345vY on 2006-11-13
Didn't work for me.  I don't have the libfreetype.so.6.3.8.  I only have libfreetype.so.6.3.10 in another location and that doesn't do the trick.

I removed 2.0.4 and installed 2.0.2 from Dapper, which didn't work either.  
Any ideas where I can get the libfreetype.so.6.3.8 library?

---

### Post by okl on 2006-11-13
!It's not working with 6.3.10-version! 
You need 6.3.8 from dapper:

You can download it here:

[http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb)

okl

---

### Post by Yv12345vY on 2006-11-13
> **okl said:**
> !It's not working with 6.3.10-version! 
You need 6.3.8 from dapper:

You can download it here:

[http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb)

okl

Thanks ok1.  I just installed and still can't find the libfreetype.so.6.3.8 file...

---

### Post by fotakis on 2006-11-13
Hello dude,

You don't have to install the freetype package, just extract the contents of the .deb file, and copy libfreetype.so.6.3.8 /usr/local/lib/ then follow the directions that okl gave.

and don't forget LD_PRELOAD before running it.

---

### Post by Yv12345vY on 2006-11-13
> **fotakis said:**
> Hello dude,

You don't have to install the freetype package, just extract the contents of the .deb file, and copy libfreetype.so.6.3.8 /usr/local/lib/ then follow the directions that okl gave.

and don't forget LD_PRELOAD before running it.

Worked!  Thanks a lot for your help :-)

---

### Post by fotakis on 2006-11-13
No problem man, I am a real newb so I am glad I could finally help my first person!!!

Cheers

---

### Post by Yv12345vY on 2006-11-13
I hear ya man.  It's a good feeling!

---

### Post by jferrando on 2006-11-26
Here's my experience:
- Removed edgy openoffice packages
- Donwloaded openoffice packeges (current v2.04 version), only found RPMs. Alienized them, installed.
- Using LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8 /opt/openoffice.org2.0/program/swriter I can see nicely hinted fonts now.
- OpenOffice is far more stable than edgy bundbled version

However, opening openoffice from konqueror clicking on a file, does not preload the library. Is there any way to configure it to preload the library.
Any upgrade from the developers expected soon?

---

### Post by otto67 on 2006-12-01
I solved the font problem as OKL indicated but with little variation.
Problem was that with edgy package of OO i had no change at all with the (pre)command:
„LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8“. 
Nothing changed also with current package of OOO 2.0.4 for debian (DEBS)
Since OOO 2.0.2 i had similar font problem in Dapper too. And there i've found the way out simply installing the OOO 2.0.1. In my „Edgy“ the simple install of OOO 2.0.1 didn't help.
So I got solution in this way:

	1.  Deinstall all openoffice packages from edgy
2.Download [http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.1.10-1ubuntu2.2_i386.deb)
3.Open the file as root in file-roller.
4.Open data.tar.gz
5.Go -> /./usr/lib
6.Unpack only libfreetype.so.6.3.8 to /usr/local/lib/

7.Get the OOO 2.0.1 or 2.0.0 debian packages from internet.
8.unpack OO... to Desktop
9.cd ~/Desktop/DEBS
10.dpkg --install *.deb 

11.Go as root to the folder /opt/openoffice2.0/program
12.Open file swriter with gedit and save it as swriter2
13.Delete all in the new file exept 1 row on the top (#bin/sh)
14.Insert in the file following text:
LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8 /opt/openoffice.org2.0/program/swriter
15.Save the file

16.Open „Preferences - Menu redactor“ ( if you have trouble using menu redactor in edgy look: [http://ubuntuforums.org/showthread.php?t=293410&page=2](http://ubuntuforums.org/showthread.php?t=293410&page=2)  )
17.Go to „Office“
18.Double click on „Openoffice2.0 Writer“
19.Change the command line to: /opt/openoffice.org2.0/program/swriter2
20.Close
If you click now „Office – Openoffice.org 2.0 Writer“ you will have all the fonts like in default system with exact rendering. On my IBM R40 the OOO 2.0.1 version runs a lot quicker than problematic 2.0.4 even with quickstart enabled.

Repeat the process 11.-15. with every program file (scalc, sdraw, simpress, sbase) in /opt/openoffice2.0/program directory.
Repeat also process 16. - 20. with every OO entry in Gnome menu

It is not the most elegant way to resolve this ugly OO font problem but at least i can now do and see what i want.
Here are screenshots too

---

### Post by shuttleworthwannabe on 2006-12-03
Hi There

This is well and good, but I do not have the luxury of highspeed, to get the 100MB odd megs of the OOO version you are recommending. We live in the "third" world, so is there a easier way to to do this? Like downlaoding a patch???

I have copied MSttcorefonts from the Windows partition into my .fonts folder and using Tahoma; this font looks really good on my 1920x1200 widescreen ATI driver without smoothing or antialiasing (AA). I prefer AA switched off. 

If I keep sans font with AA swicthed on, the fint menu in OOO is rendered fine, but I prefer AA off.

Any help will be appreciated.

swb

---

### Post by otto67 on 2006-12-08
Sorry - little comment to my previous message
No need to make additional scripts swriter2, scalc2 etc.
It's also working when you go: /opt/openoffice.org2.0/program
as root make the file "soffice" writable
then open the file with gedit and add as 2nd row:
export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8

Then save it and you should have all nice fonts in every ooo2.0 applications (scalc, swriter, simpress etc). No need for additional scripts.

In my Edgy it is working with OOO 2.0.0 and 2.0.1
Versions 2.0.2 - 2.0.4 give not working with this trick - always ugly fonts

---

### Post by Akre on 2006-12-10
I have got very similar problem. Font rendering was a mess, especially letters like y,z,x,n. Environment: Edgy|64bit|laptop LCD

What helped in my case was tampering with
sudo dpkg-reconfigure fontconfig-config

And then choosing:
Native
Automatic
Yes  |No - this one shouldn't make difference.

Then fonts started looking good (only good, OO fonts could still look better but they are at least acceptable now) in all applications: oo, kword, ff etc..
Funny thing, tampering with this setting allowed me to reproduce behavior in Kword (broken rendering)

Anyway, I think it is worth experimenting with this config.

---

