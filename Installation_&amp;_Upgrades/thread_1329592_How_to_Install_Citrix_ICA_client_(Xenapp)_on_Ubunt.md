---
title: "How to Install Citrix ICA client (Xenapp) on Ubuntu netbook remix"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by varspare on 2009-11-17
*now tested on 10.4 - first tested on 8.10* Also tested against 10.04 LTS (standard Desktop release)

Hi all,

I did this originally some time ago now and documented it (force of habit), one of my colleagues suggested I post it up here for anyone who might need it.

This is a step-by-step guide to installing the Citrix ICA client on Ubuntu it has worked on 8.10 and 9.10 for me, and will hopefully save you a bit of time. 

(quick note on formating- anything with a #(hash) should be typed on the command line and without the #(hash) character.)

[COLOR=DarkGreen]Note: There is now a Debian (Ubuntu) package for the ICA client (linuxx86-11.100.158406.deb) which you may use instead of the package this guide is using linuxx86-11.100.158406.tar.gz, if you would prefer to use the .deb package then just ignore the steps for gzip and tar, although all other steps are still relevant.[/COLOR]

**_How to install the citrix xenapp client on ubuntu _**

1. point your browser to the Citrix download site at
[U][http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860#top)
[/U]
and download the tar.gz file, which should give you linuxx86-11.100.158406.tar.gz

2.point your browser to the security certificates at
[http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm](http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm)
and download both;
thawte-server-ca.crt
and
ThawteRoot.crt

3. put all 3 of these files in ~/Downloads 
i.e. 
 ~/Dowloads/linuxx86-11.100.158406.tar.gz
 ~/Dowloads/thawte-server-ca.crt
 ~/Dowloads/ThawteRoot.crt

4. Open a terminal

5. using the terminal we will install Openmotif (at the time of writing version 3 is the latest available)
in the terminal type 
#sudo apt-get install libmotif3

(I was able to omit this step (6.) on 9.10 but I'll leave it in for completeness)
6. with that done we need to create a new symbolic link so that the menu shortcut will launch.
again from the terminal
#sudo ln -s /usr/lib/libXm.so.3.0.2 /usr/lib/libXm.so.4

7.Now back to our ~/Downloads folder
#cd ~/Downloads

8.We now need to unpack our Citrix client installer 
gunzip will uncompress the file
#gunzip ./linuxx86-11.100.158406.tar.gz
and tar will remove the packaging
#tar xvf ./linuxx86-11.100.158406.tar

9.to install the Citrix client type we need to launch the installer
#sudo ./setupwfc

10. select option 1 to install the client

11. when prompted enter the location to install the client as;
/usr/lib/ICAClient

12. press y when prompted to agree to install the client

12. press 1 when prompted to accept the license conditions

13. otherwise accept the defaults

14. once the installation is complete exit the installer this will be from the options screen so select option 3 when ready.

15. now we need to setup the SSL certificates by copying them into the newly created directory if everything has gone to plan this should be /usr/lib/ICAClient/keystore/cacerts/

#sudo cp ~/Downloads/thawte-server-ca.crt /usr/lib/ICAClient/keystore/cacerts/thawte-server-ca.crt 
#sudo cp ~/Downloads/ThawteRoot.crt /usr/lib/ICAClient/keystore/cacerts/ThawteRoot.crt 

16. The citrix client should now be working properly so point your web browser to your Citrix Access Gateway login and try it out.




Attached is a tar of all the files I used (except for the xenapp installer) with a copy of the instructions. To untar it run 
#tar -xvf citrix_install_linux.tar

---

### Post by nkle004 on 2009-11-30
Fantastic work, I am new and it really helped me figure out how to install Citrix.
I have one trouble here I am not able to execute step 5. I am getting some error saying motiff not found.
Do I need to do anything before running that step 5 ? I just installed Ubuntu 9.10 and this is my installation. The first thing I did is to install Citrix because I can't leave without it I have to do work from home almost twice a week.

Thanks in advance for your help

---

### Post by varspare on 2009-12-13
Hi 

glad to have helped you

one thing I've noticed is your error message;
> **nkle004 said:**
> I am not able to execute step 5. I am getting some error saying motiff not found.

I'm presuming slightly that it looks like this;
user@computer-name:~$ sudo apt-get install libmotiff3
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 E: Couldn't find package libmotiff3

could it be a typo there is only the one 'f'

if you copy the line (excluding the hash) and paste it into the terminals command line and execute it will ask for you're password then hunt through the repositories and then install the libmotif3 package.

unless you've already successfully installed it in which case it'll look like this;

user@computer-name:~$ sudo apt-get install libmotif3
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmotif3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@computer-name:~$ 


Hope that helps

---

### Post by inkhorn on 2010-03-09
Thanks a bunch for this tutorial!  I just started working for an organization that uses Citrix Xenapp for remote desktop administration.  Now I can use all my work applications (all are Windows apps) on my Ubuntu machine at home :)

Cheers,
Inkhorn

---

### Post by likerice on 2010-04-30
Great tutorial.

The instructions continue to work without a hitch for lucid lynx (10.04).

Thank you!

---

### Post by paulec on 2010-05-04
Thanks great tutorial.

To add a couple of things.
I found I need to copy the files from /usr/share/ca-certificates/mozilla/ to /usr/lib/ICAClient/keystore/cacerts/ so I could access my company system.  A symbolic link may be a better solution.  I haven't tried that one yet.

Also Citrix has a deb package available for the latest version icaclient_11.100_i386.patched.deb  that make the whole process much easier.

Leck

---

### Post by varspare on 2010-05-08
Thanks to all of you for your helpful feedback,
particular thanks to Likerice- I've just completed testing on 10.04 myself and found no issues
Thank Paulec, I'll have a look into both your suggestions.

---

### Post by nhovan on 2010-05-20
so i got this to work on my 10.04 netbook remix and it works perfectly.
i am trying to put this on my laptop that is running the full 10.04 version and it just hangs.
i followed the instructions to a T and have everything in the proper folders. when i get into the citrix portion to kick off a RDP session to my windows desktop the Citrix Receiver doesnt kick off it just sits.
i cant consult work support because linux isnt supported. 

can anyone help?

---

### Post by Pan Sloboda on 2010-05-21
Great job, I just switched from Vista to 10.04 and need Citrix working, and now it does!

Chris

---

### Post by disgruntlednoob on 2010-06-04
Hey, So I've followed your instructions and all seemed to be ok but when I went to open the launch.ica file from my companies website there was no program associated with the filetype. i tried using /usr/lib/ICAClient/wfica but nothing happened. 

Any suggestions would be greatly appreciated. 

Note: please speak slowly and clearly - I am very new to linux!

---

### Post by varspare on 2010-06-12
Hi all,
thanks for the posts,

For those of you having trouble, I haven't tested on the standard release yet, however I am in the process of building a new machine, so I will test it out and let you know what I find.

In lieu of that, have you tried step 6?;
#sudo ln -s /usr/lib/libXm.so.3.0.2 /usr/lib/libXm.so.4
(check with #ls -l /usr/lib/libXm.so.4)

If that doesn't fix it check to see if this link exists
run 
#ls -l /usr/lib/mozilla/plugins/npica.so
       It should give you the following output;
lrwxrwxrwx 1 root root 27 DATE TIME /usr/lib/mozilla/plugins/npica.so -> /usr/lib/ICAClient/npica.so

If not you can create it with
#sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla/plugins/npica.so


good luck

Varspare

---

### Post by varspare on 2010-06-12
Right, I've built a brand new machine and tested it with the standard release of Ubuntu (10.04 LTS). The instructions worked perfectly. The only difference I found was that I had to create the ~/Downloads directory.

If your version is not working try reinstalling the libmotif3 package.

varspare

---

### Post by techdoc48 on 2010-08-01
I am as green as can be with UBUNTU.

I don't know if I did something wrong or what?

I can log into CITRIX but when I try to run an application, I get an error message:

**Client Error**
[COLOR=Blue]You have not chosen to trust "UTN-USERFirst-Hardware" the issuer of the server's
security certificate (SSL error 61).[/COLOR]

Can any one tell me what to do to fix this problem.

Thanks 
techdoc48

---

### Post by nc_jed on 2010-08-01
> **techdoc48 said:**
> I am as green as can be with UBUNTU.

I don't know if I did something wrong or what?

I can log into CITRIX but when I try to run an application, I get an error message:

**Client Error**
[COLOR=Blue]You have not chosen to trust "UTN-USERFirst-Hardware" the issuer of the server's
security certificate (SSL error 61).[/COLOR]

Can any one tell me what to do to fix this problem.

Thanks 
techdoc48

Does this post help?  [http://blog.torh.net/2008/02/29/problems-with-citrix-client-on-linux/](http://blog.torh.net/2008/02/29/problems-with-citrix-client-on-linux/)

- Jed

---

### Post by techdoc48 on 2010-08-05
Thank you very much.
That link gave all the info I needed.

Found and copied needed crt and we are off to the races.

techdoc48 :p

---

### Post by vangop on 2010-09-06
Anybody managed to work with the full-screen mode?
On win full-screen mode can be cancelled by Shift+F2, here this shortcut doesn't work, and I'm stuck with remote machine forever :)

Found a solution:
[this post]("http://ubuntuforums.org/showpost.php?p=7064099&postcount=4")

---

### Post by greenchilli on 2010-09-17
When selecting the companies available applications I also get the "Open launch.ica" dialogue.
I tried using /usr/lib/ICAClient/wfica and it worked perfectly.

All my links are in place as the tutorial instructed. 

This is a well documented tutorial.

---

### Post by ssx106 on 2010-09-29
I have followed the instruction on this page and downloaded libmotif3.  I connect to the server all right.  The application open and I can logon to it.  Then I found the buttons not responding.  

It seemed the cursor and the botton location is "out of sync".  While I point and click a button below a drop-box, the button did not respond.  Instead the drop box responded by droping a list of choices.  Then I found most button not functioning correctly.  Fortunately, the top menu still function so that I can logoff.  

I had this once.  At that time, I thought that I had downloaded the wrong version of Open Motif as specified on the Citrix download page.  This time I follow this instruction and downloaded libmotif3 as mentioned in another post.  Is it true that the problem is with libmotif3?  If so, can any one tell me what libmotif&#12288;I should download?  Or, would someone please kind enough to tell me what have I done wrong?  Many thanks.  I'm running Ubuntu 10.04 netbook remix on a USB finger.

---

### Post by nc_jed on 2010-10-03
> **ssx106 said:**
> It seemed the cursor and the botton location is "out of sync".  While I point and click a button below a drop-box, the button did not respond.  

This has happened to me a couple of times on our web delivered versions of Dameware Mini Remote.  I think in my case, I was running 2 copies of it simultaneously.  Make sure if you are opening your app on an intranet/internet page, you only click it once as in a weblink.  In the Citrix Program Neighborhood, you have to click it twice (as in a Desktop application).

- Jed

---

### Post by Jakob Sundbøl on 2010-10-04
Hello Forum! 
I hope you can help me with getting my Citrix Receiver to work. Although I have followed the advice on these pages, I can't make it work. I still get an SSL error 61 when I try to connect to my company's citrix from home. 

The error message says: 
You have not chosen to trust "Verisign Class 3 Secure Server CA", the issuer of the server's security certificate (SSL error 61). 

What I have done: 
[LIST]
[*]I am running Lynx 10.04 - Lucid Lynx
[*]I have downloaded and installed the Citrix Receiver 11.100 from [http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755) 
[*]I have installed openmotif3 
[*]I have runned the ldd-check and made a soft link between x3 and x4 as described earlier in this thread. 
[*]I have downloaded and saved the Thawte-certificate as described earlier in this thread. 
[*]Furthermore, I have copied the certificate named Verisign_Class_3_Public (etc) from usr/share/ca-certificates/mozilla to /usr/lib/ICAClient/keystore/cacerts
[/LIST]Can anybody in here help me by explaining why it still doesn't work? 

Thanks in advance!

---

### Post by nc_jed on 2010-10-04
did you make sure the 'ca-certificates' package was installed?   > **Jakob Sundbøl said:**
> Hello Forum! 
I hope you can help me with getting my Citrix Receiver to work. Although I have followed the advice on these pages, I can't make it work. I still get an SSL error 61 when I try to connect to my company's citrix from home. 

The error message says: 
You have not chosen to trust "Verisign Class 3 Secure Server CA", the issuer of the server's security certificate (SSL error 61). 

What I have done: 
[LIST]
[*]I am running Lynx 10.04 - Lucid Lynx
[*]I have downloaded and installed the Citrix Receiver 11.100 from [http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755) 
[*]I have installed openmotif3 
[*]I have runned the ldd-check and made a soft link between x3 and x4 as described earlier in this thread. 
[*]I have downloaded and saved the Thawte-certificate as described earlier in this thread. 
[*]Furthermore, I have copied the certificate named Verisign_Class_3_Public (etc) from usr/share/ca-certificates/mozilla to /usr/lib/ICAClient/keystore/cacerts
[/LIST]Can anybody in here help me by explaining why it still doesn't work? 

Thanks in advance!

---

### Post by Jakob Sundbøl on 2010-10-06
Thank you for your quick reply! 
The ca-certificates was already installed. I installed the ca-certificates-java and now I receive a different error message: "An error occured while making the requested connection" (as shown in screendump). 

Any suggestions?

---

### Post by nc_jed on 2010-10-31
> **nc_jed said:**
> This has happened to me a couple of times on our web delivered versions of Dameware Mini Remote.  I think in my case, I was running 2 copies of it simultaneously.  Make sure if you are opening your app on an intranet/internet page, you only click it once as in a weblink.  In the Citrix Program Neighborhood, you have to click it twice (as in a Desktop application).

- Jed

I found a solution to this.  When it happens for me, the Dameware toolbar appears twice -- slightly offset from each other.  I've found that switching desktops from one to 2 (or vice versa) clears up this issue (the window seems pinned, so it is available in both).

- Jed

---

### Post by nc_jed on 2010-10-31
> **Jakob Sundbøl said:**
> Thank you for your quick reply! 
The ca-certificates was already installed. I installed the ca-certificates-java and now I receive a different error message: "An error occured while making the requested connection" (as shown in screendump). 

Any suggestions?

From what I see on Google, this seems like an issue on the server.  Does the function work from a Windows machine?  I assume you've seen this post from Citrix support site, but if not, take a look:  [http://support.citrix.com/article/CTX123003](http://support.citrix.com/article/CTX123003)

- Jed

---

### Post by njigsaw on 2010-11-04
Another cry for help.

On the upgrade to Ubuntu version 10.whatever LTS my ability to use Citrix Receiver appears to have died.
I previously had everything running fine and when I logged onto my work site remotely I could select the various packages Outlook, Explorer, SAP etc OK, Citrix Receiver would pop up and away I went using the package remotely.

Now when I log onto my work site and try and select a package to open i get no error messages I just see Firefox telling me "loading" and thats it. Citrix Receiver doesnt even kick in.

As far as I can tell Ive done everything recommended with loading Citrix 11.0 making sure libmotif3 files exist, Thawtes certificates are in teh right place and now Im at a loss.

I can still get on and operate receiver on my other linux laptops/ desktops so dont think there is anything silly happening from the work side of the system.


Any ideas please?

Thanks 

neal

---

### Post by claven123 on 2010-11-11
I followed the directions in the first post.  However, when I click on the thwart files at the sanford site it states they are already installed.  Do I still need to DL them?  I was not given an option to dl them.

When I open firefox and click on the area to access I get nothing, just done at the bottom of the window.




Below is the transcript of the installation process.


dennis@dennis-Desktop:~$ sudo apt-get install libmotif3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libmotif3
0 upgraded, 1 newly installed, 0 to remove and 85 not upgraded.
Need to get 1,314kB of archives.
After this operation, 3,244kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse libmotif3 i386 2.2.3-4 [1,314kB]
Fetched 1,314kB in 3s (375kB/s)      
Selecting previously deselected package libmotif3.
(Reading database ... 127426 files and directories currently installed.)
Unpacking libmotif3 (from .../libmotif3_2.2.3-4_i386.deb) ...
Setting up libmotif3 (2.2.3-4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dennis@dennis-Desktop:~$ sudo ln -s /usr/lib/libXm.so.3.0.2 /usr/lib/libXm.so.4
dennis@dennis-Desktop:~$ cd ~/Downloads
dennis@dennis-Desktop:~/Downloads$ gunzip ./linuxx86-11.100.158406.tar.gz
dennis@dennis-Desktop:~/Downloads$ tar xvf ./linuxx86-11.100.158406.tar
./PkgId
./setupwfc
./nls/
./nls/ja/
./nls/ja/eula.txt
./nls/ja/hinst.msg
./nls/ja/install.txt
./nls/ja/UTF-8/
./nls/ja/UTF-8/setupwfc.msg
./nls/ja/setupwfc.msg
./nls/ja/readme.txt
./nls/en/
./nls/en/eula.txt
./nls/en/hinst.msg
./nls/en/install.txt
./nls/en/UTF-8/
./nls/en/UTF-8/setupwfc.msg
./nls/en/setupwfc.msg
./nls/en/readme.txt
./nls/de/
./nls/de/eula.txt
./nls/de/hinst.msg
./nls/de/install.txt
./nls/de/UTF-8/
./nls/de/UTF-8/setupwfc.msg
./nls/de/setupwfc.msg
./nls/de/readme.txt
./linuxx86/
./linuxx86/linuxx86.psf
./linuxx86/hinst
./linuxx86/echo_cmd
./linuxx86/linuxx86.cor/
./linuxx86/linuxx86.cor/util/
./linuxx86/linuxx86.cor/util/xcapture
./linuxx86/linuxx86.cor/util/what
./linuxx86/linuxx86.cor/util/pacexec
./linuxx86/linuxx86.cor/util/hinst
./linuxx86/linuxx86.cor/util/sunraymac.sh
./linuxx86/linuxx86.cor/util/echo_cmd
./linuxx86/linuxx86.cor/util/libgstflatstm.so
./linuxx86/linuxx86.cor/util/pnabrowse
./linuxx86/linuxx86.cor/util/gst_play
./linuxx86/linuxx86.cor/util/nslaunch
./linuxx86/linuxx86.cor/util/pac.js
./linuxx86/linuxx86.cor/util/icalicense.sh
./linuxx86/linuxx86.cor/CHARICONV.DLL
./linuxx86/linuxx86.cor/config/
./linuxx86/linuxx86.cor/config/plugin.ini
./linuxx86/linuxx86.cor/config/All_Regions.ini
./linuxx86/linuxx86.cor/config/regions.ini
./linuxx86/linuxx86.cor/config/Unknown_Region.ini
./linuxx86/linuxx86.cor/config/Untrusted_Region.ini
./linuxx86/linuxx86.cor/config/canonicalization.ini
./linuxx86/linuxx86.cor/config/Trusted_Region.ini
./linuxx86/linuxx86.cor/config/usertemplate/
./linuxx86/linuxx86.cor/config/usertemplate/All_Regions.ini
./linuxx86/linuxx86.cor/config/usertemplate/Unknown_Region.ini
./linuxx86/linuxx86.cor/config/usertemplate/Untrusted_Region.ini
./linuxx86/linuxx86.cor/config/usertemplate/Trusted_Region.ini
./linuxx86/linuxx86.cor/usb/
./linuxx86/linuxx86.cor/usb/usb.conf
./linuxx86/linuxx86.cor/usb/VDGUSB.DLL
./linuxx86/linuxx86.cor/usb/ctxusbd
./linuxx86/linuxx86.cor/usb/ctxusbd.rc
./linuxx86/linuxx86.cor/usb/ctxusb
./linuxx86/linuxx86.cor/usb/ctx_usb_isactive
./linuxx86/linuxx86.cor/usb/ica-usb.rules
./linuxx86/linuxx86.cor/SPEEX.DLL
./linuxx86/linuxx86.cor/npica.so
./linuxx86/linuxx86.cor/wfica
./linuxx86/linuxx86.cor/libproxy.so
./linuxx86/linuxx86.cor/VDSPMIKE.DLL
./linuxx86/linuxx86.cor/wfcmgr
./linuxx86/linuxx86.cor/icons/
./linuxx86/linuxx86.cor/icons/session.xpm
./linuxx86/linuxx86.cor/icons/manager.png
./linuxx86/linuxx86.cor/PDCRYPT1.DLL
./linuxx86/linuxx86.cor/help/
./linuxx86/linuxx86.cor/VORBIS.DLL
./linuxx86/linuxx86.cor/NDS.DLL
./linuxx86/linuxx86.cor/libctxssl.so
./linuxx86/linuxx86.cor/ADPCM.DLL
./linuxx86/linuxx86.cor/VDMM.DLL
./linuxx86/linuxx86.cor/TW1.DLL
./linuxx86/linuxx86.cor/nls/
./linuxx86/linuxx86.cor/nls/ja/
./linuxx86/linuxx86.cor/nls/ja/module.ini
./linuxx86/linuxx86.cor/nls/ja/wfclient.ini
./linuxx86/linuxx86.cor/nls/ja/pna.nls
./linuxx86/linuxx86.cor/nls/ja/XCapture.ad
./linuxx86/linuxx86.cor/nls/ja/appsrv.ini
./linuxx86/linuxx86.cor/nls/ja/Wfcmgr
./linuxx86/linuxx86.cor/nls/ja/index.htm
./linuxx86/linuxx86.cor/nls/ja/eula.txt
./linuxx86/linuxx86.cor/nls/ja/Wfica
./linuxx86/linuxx86.cor/nls/ja/Npica.ad
./linuxx86/linuxx86.cor/nls/ja/UTF-8/
./linuxx86/linuxx86.cor/nls/ja/UTF-8/pna.nls
./linuxx86/linuxx86.cor/nls/ja/UTF-8/XCapture.ad
./linuxx86/linuxx86.cor/nls/ja/UTF-8/Wfcmgr
./linuxx86/linuxx86.cor/nls/ja/UTF-8/eula.txt
./linuxx86/linuxx86.cor/nls/ja/UTF-8/Wfica
./linuxx86/linuxx86.cor/nls/en/
./linuxx86/linuxx86.cor/nls/en/module.ini
./linuxx86/linuxx86.cor/nls/en/wfclient.ini
./linuxx86/linuxx86.cor/nls/en/pna.nls
./linuxx86/linuxx86.cor/nls/en/XCapture.ad
./linuxx86/linuxx86.cor/nls/en/appsrv.ini
./linuxx86/linuxx86.cor/nls/en/Wfcmgr
./linuxx86/linuxx86.cor/nls/en/index.htm
./linuxx86/linuxx86.cor/nls/en/eula.txt
./linuxx86/linuxx86.cor/nls/en/Wfica
./linuxx86/linuxx86.cor/nls/en/Npica.ad
./linuxx86/linuxx86.cor/nls/en/UTF-8/
./linuxx86/linuxx86.cor/nls/en/UTF-8/pna.nls
./linuxx86/linuxx86.cor/nls/en/UTF-8/XCapture.ad
./linuxx86/linuxx86.cor/nls/en/UTF-8/Wfcmgr
./linuxx86/linuxx86.cor/nls/en/UTF-8/eula.txt
./linuxx86/linuxx86.cor/nls/en/UTF-8/Wfica
./linuxx86/linuxx86.cor/nls/de/
./linuxx86/linuxx86.cor/nls/de/module.ini
./linuxx86/linuxx86.cor/nls/de/wfclient.ini
./linuxx86/linuxx86.cor/nls/de/pna.nls
./linuxx86/linuxx86.cor/nls/de/XCapture.ad
./linuxx86/linuxx86.cor/nls/de/appsrv.ini
./linuxx86/linuxx86.cor/nls/de/Wfcmgr
./linuxx86/linuxx86.cor/nls/de/index.htm
./linuxx86/linuxx86.cor/nls/de/eula.txt
./linuxx86/linuxx86.cor/nls/de/Wfica
./linuxx86/linuxx86.cor/nls/de/Npica.ad
./linuxx86/linuxx86.cor/nls/de/UTF-8/
./linuxx86/linuxx86.cor/nls/de/UTF-8/pna.nls
./linuxx86/linuxx86.cor/nls/de/UTF-8/XCapture.ad
./linuxx86/linuxx86.cor/nls/de/UTF-8/Wfcmgr
./linuxx86/linuxx86.cor/nls/de/UTF-8/eula.txt
./linuxx86/linuxx86.cor/nls/de/UTF-8/Wfica
./linuxx86/linuxx86.cor/PDCRYPT2.DLL
./linuxx86/linuxx86.cor/VDSCARD.DLL
./linuxx86/linuxx86.cor/VDMSSPI.DLL
./linuxx86/linuxx86.cor/VDHSSPI.DLL
./linuxx86/linuxx86.cor/keyboard/
./linuxx86/linuxx86.cor/keyboard/dec401uk.kbd
./linuxx86/linuxx86.cor/keyboard/hpintps2.kbd
./linuxx86/linuxx86.cor/keyboard/dcint401.kbd
./linuxx86/linuxx86.cor/keyboard/hpuk101.kbd
./linuxx86/linuxx86.cor/keyboard/sgindyus.kbd
./linuxx86/linuxx86.cor/keyboard/sparc5.kbd
./linuxx86/linuxx86.cor/keyboard/decpcx.kbd
./linuxx86/linuxx86.cor/keyboard/dcintpcx.kbd
./linuxx86/linuxx86.cor/keyboard/dguk.kbd
./linuxx86/linuxx86.cor/keyboard/sparc6usb.kbd
./linuxx86/linuxx86.cor/keyboard/linux-ja.kbd
./linuxx86/linuxx86.cor/keyboard/agex2.kbd
./linuxx86/linuxx86.cor/keyboard/sparcfr5.kbd
./linuxx86/linuxx86.cor/keyboard/sg.kbd
./linuxx86/linuxx86.cor/keyboard/sparcfr4.kbd
./linuxx86/linuxx86.cor/keyboard/sgindyfr.kbd
./linuxx86/linuxx86.cor/keyboard/hpusitf.kbd
./linuxx86/linuxx86.cor/keyboard/ncdn-101.kbd
./linuxx86/linuxx86.cor/keyboard/dgus.kbd
./linuxx86/linuxx86.cor/keyboard/hpukitf.kbd
./linuxx86/linuxx86.cor/keyboard/dg.kbd
./linuxx86/linuxx86.cor/keyboard/sgindyuk.kbd
./linuxx86/linuxx86.cor/keyboard/sparcus3.kbd
./linuxx86/linuxx86.cor/keyboard/sparcgr5.kbd
./linuxx86/linuxx86.cor/keyboard/netbsd.kbd
./linuxx86/linuxx86.cor/keyboard/hpus101.kbd
./linuxx86/linuxx86.cor/keyboard/sparc3.kbd
./linuxx86/linuxx86.cor/keyboard/hp101.kbd
./linuxx86/linuxx86.cor/keyboard/scoos5.kbd
./linuxx86/linuxx86.cor/keyboard/ncdn-102.kbd
./linuxx86/linuxx86.cor/keyboard/hpgritf.kbd
./linuxx86/linuxx86.cor/keyboard/sparc4.kbd
./linuxx86/linuxx86.cor/keyboard/linux.kbd
./linuxx86/linuxx86.cor/keyboard/scouw2.kbd
./linuxx86/linuxx86.cor/keyboard/sparcus5.kbd
./linuxx86/linuxx86.cor/keyboard/hpps2.kbd
./linuxx86/linuxx86.cor/keyboard/sngr.kbd
./linuxx86/linuxx86.cor/keyboard/hpfritf.kbd
./linuxx86/linuxx86.cor/keyboard/sgindygr.kbd
./linuxx86/linuxx86.cor/keyboard/sparcuk4.kbd
./linuxx86/linuxx86.cor/keyboard/dec401.kbd
./linuxx86/linuxx86.cor/keyboard/dcuspcx.kbd
./linuxx86/linuxx86.cor/keyboard/hpint101.kbd
./linuxx86/linuxx86.cor/keyboard/hpukps2.kbd
./linuxx86/linuxx86.cor/keyboard/trimodal.kbd
./linuxx86/linuxx86.cor/keyboard/age2.kbd
./linuxx86/linuxx86.cor/keyboard/decpcxuk.kbd
./linuxx86/linuxx86.cor/keyboard/sparcus4.kbd
./linuxx86/linuxx86.cor/keyboard/mac101.kbd
./linuxx86/linuxx86.cor/keyboard/ibm.kbd
./linuxx86/linuxx86.cor/keyboard/hpitf.kbd
./linuxx86/linuxx86.cor/keyboard/dgfr.kbd
./linuxx86/linuxx86.cor/keyboard/sparcgr4.kbd
./linuxx86/linuxx86.cor/keyboard/keyboard.ini
./linuxx86/linuxx86.cor/keyboard/dcus401.kbd
./linuxx86/linuxx86.cor/keyboard/hpusps2.kbd
./linuxx86/linuxx86.cor/keyboard/dggr.kbd
./linuxx86/linuxx86.cor/keyboard/automatic.kbd
./linuxx86/linuxx86.cor/keyboard/sgindy.kbd
./linuxx86/linuxx86.cor/keyboard/sparcuk5.kbd
./linuxx86/linuxx86.cor/keystore/
./linuxx86/linuxx86.cor/keystore/cacerts/
./linuxx86/linuxx86.cor/keystore/cacerts/Class3PCA_G2_v2.crt
./linuxx86/linuxx86.cor/keystore/cacerts/BTCTRoot.crt
./linuxx86/linuxx86.cor/keystore/cacerts/SecureServer.crt
./linuxx86/linuxx86.cor/keystore/cacerts/Class4PCA_G2_v2.crt
./linuxx86/linuxx86.cor/keystore/cacerts/Pcs3ss_v4.crt
./linuxx86/linuxx86.cor/keystore/cacerts/GTECTGlobalRoot.crt
dennis@dennis-Desktop:~/Downloads$ sudo ./setupwfc
Citrix Receiver for Linux 11.100 setup.

Copyright 1996-2010 Citrix Systems, Inc. All rights reserved.

Citrix, Independent Computing Architecture (ICA), Program Neighborhood,
MetaFrame, and MetaFrame XP are registered trademarks and Citrix Receiver,
Citrix XenApp, XenDesktop, Citrix Presentation Server, Citrix Access Suite,
and SpeedScreen are trademarks of Citrix Systems, Inc. in the United States
and other countries.

Microsoft, MS, MS-DOS, Outlook, Windows, Windows NT, and BackOffice are
either registered trademarks or trademarks of Microsoft Corporation in
the United States and other countries.

All other Trade Names referred to are the Servicemark, Trademark,
or Registered Trademark of the respective manufacturers.


Select a setup option:

 1. Install Citrix Receiver for Linux 11.100
 2. Remove Citrix Receiver for Linux 11.100
 3. Quit Citrix Receiver for Linux 11.100 setup

Enter option number 1-3 [1]: 1

Please enter the directory in which Citrix Receiver for Linux is to be installed.
[default /usr/lib/ICAClient] 
or type "quit" to abandon the installation: /usr/lib/ICAClient

You have chosen to install Citrix Receiver for Linux 11.100 in /usr/lib/ICAClient.

Proceed with installation? [default n]: y

CITRIX(R) LICENSE AGREEMENT

Use of this component is subject to the Citrix license covering the 
Citrix product(s) with which you will be using this component. This 
component is only licensed for use with such Citrix product(s).

CTX_code EP_T_A34320

Select an option:

 1. I accept
 2. I do not accept

Enter option number 1-2 [2]: 1
Installation proceeding...

Checking available disk space ...

    Disk space available 46327336 K 
    Disk space required 6923 K


Continuing ...
Creating directory /usr/lib/ICAClient
Core package...
Setting file permissions...
Integrating with browsers...
Browsers found.

Integration complete.
Do you want to integrate Citrix Receiver with KDE and GNOME? [default y]: y
Do you want GStreamer to use the plugin from this client? [default y]: y
Do you want to install USB support? [default n]: n
USB support not installed.

Select a setup option:

 1. Install Citrix Receiver for Linux 11.100
 2. Remove Citrix Receiver for Linux 11.100
 3. Quit Citrix Receiver for Linux 11.100 setup

Enter option number 1-3 [2]: 3
Quitting Citrix Receiver for Linux 11.100 setup.
dennis@dennis-Desktop:~/Downloads$ 


[IMG]file:///home/dennis/Desktop/error.png[/IMG]

---

### Post by bistro on 2010-11-13
> Another cry for help.

On the upgrade to Ubuntu version 10.whatever LTS my ability to use Citrix Receiver appears to have died.
I previously had everything running fine and when I logged onto my work site remotely I could select the various packages Outlook, Explorer, SAP etc OK, Citrix Receiver would pop up and away I went using the package remotely.

Now when I log onto my work site and try and select [http://ubuntuforums.org/showthread.php?t=767222ahttp://ubuntuforums.org/showthread.php?t=767222](http://ubuntuforums.org/showthread.php?t=767222ahttp://ubuntuforums.org/showthread.php?t=767222) package to open i get no error messages I just see Firefox telling me "loading" and thats it. Citrix Receiver doesnt even kick in.

I had same problem, after reading

[http://ubuntuforums.org/showthread.php?t=767222](http://ubuntuforums.org/showthread.php?t=767222)

I replaced icedtea java with sun java and that  solved it.

---

