---
title: "Installation Pass Update fail"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by JonesK on 2012-11-16
Hi All, new to Ubuntu.....I work for an ISp and looking to mess around with ubuntu to gain some experience so I decided to Jump Straight into it.....I've worked on Linux briefly before very limited - checking radius logs on authentication and adding mailboxes etc on the command line.

Very interested in getting into the nitty gritty.....soooooo I decided to grab a pc at home, format it and get started......

I followed a Document i researched on the net.

I want to build a webserver to mess around on. 

So from the start : Downloaded Linux server 7.10 ISO

- Burned Image to Disc
- Ran installation on PC
- Named the Server
- Set the passwords
- Onboard Lan Faulty so I installed a spare 4 port Network card i bought a couple of months back
- Set port 1 as primary port
- Linux picked up DHCP and auto configured card
- no proxy
- Installed LAMP only when prompted what to install as per document


OK now basic setup installed
- Restarted
- Time to get Updated
 
I log in, Do an ifconfig to verify that ip's are set
all working

- can ping Default gateway
- can ping external websites hostnames as well as IP's (so there is connectivity)

-As per document I log in as su 
Locate /etc/apt/sources.list
vi sources.list
delete all lines pertaining to "deb cdrom" so that the updater does not look for updates from the cdrom

delete 2 or 3 lines and alls good

Time to Update

- type : apt-get update as per document and most other references on the net
Result : "Reading package lists........Done"

- type: apt-get upgrade to download and install
Result :

"Reading package lists........Done"
'Building Dependancy tree'
"reading state information......done"
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"

Now I'm lost as this is an old version, sureley theres updates?
Is there possibly anything thats blocking the download and updates?

Anyway so I decide lets skip updates for now and move onto the next step

Type IP of Server on seperate pc on the LAN - "IT WORKS" message

Next step

Installing Telnet

Type: apt-get install telnetd

(assuming it should download and install telnet)

Result : 
"Reading package lists........Done"
'Building Dependancy tree'
"reading state information......done"
"E: couldn't find telnetd"

Now I'm stumped and swearing big words 

Is there anything that i'm missing? 

Running an ADSL connection from the router to a switch. Switch distributes connectivity to 4 PC's, one of them being this Linux box

Any help would be appreciated! :popcorn:

---

### Post by arpanaut on 2012-11-16
7.10 is extremely out-dated, and is no longer supported.
Hence your inability to get updates, it's possible, but not worth it.

I would recommend that you download a later version that has Long Term Support = LTS
Such as 10.04 or 12.04 server iso and install from there. 
Both have support for 5 years from release and are much more up to date.
The How To you are trying to follow is old but the basics are probably the same, but you may want to look for a more current guide.

---

### Post by ajgreeny on 2012-11-16
Server version 7.10 is no longer supported so there is no point trying any longer with that.  Why did you download that version and not the most recent long term support version?

You should try the server version of 12.04 for the longest possible support time, until April 2017, I think, the same as the desktop version.

When support disappears from a version of ubuntu the repositories are removed (from their original spot) and go to the EOL repos which yOu can find out about at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades), but as you've only just installed it will be much quicker and more economical of bandwidth to start again.

---

### Post by JonesK on 2012-11-16
No problem, was thinkin about something along those lines of it being EOL.

What would you guys suggest? 10 or 12? are there hecticly major differences with the install and updates as well as more supported things that one can do with 12 rather than 10? or for my purpose would it be ok for either one?

Purpose is just to get the feel for it and mess around before i decide to do my certification

---

### Post by Old_Grey_Wolf on 2012-11-16
> **JonesK said:**
> 
What would you guys suggest? 10 or 12? 

I would use 12.04 which is supported until April 2017. 10.04 is only supported for another 6 months or April 2013.

---

### Post by JonesK on 2012-11-16
Great...lets try this again! Thanks for all the input guys much appreciated!

---

### Post by JonesK on 2012-11-19
so I managed to get 10.04 installed as 12 wouldnt work on this old thing.........logged in as normal user, but need to log in as su to updates and access certain folders.....am I missing something as when i did the installation i was only asked to put in 1 password, now its asking for su password and the password that i used during initial setup doesnt work? 

do i need to install extra goodies?

---

### Post by Old_Grey_Wolf on 2012-11-19
Read this about root and su in Ubuntu. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JonesK on 2013-02-08
Soo, after a while I have some more free time, As said before, I got Ubuntu 10 loaded, now for the fun.......

log in as su

run the update, update runs for an hour

now from the document that I'm following it says that if I should access the IP of the server from one of the pc's on the LAN i should get "[FONT=&quot]web page with a link to apache2-default, and clicking on the link will bring up a brief message[/FONT]"

however I get a "webpage cannot be displayed" Message ????

Nevertheless, eager as a newbee, I continue with the installation:

 [FONT=&quot]Type apt-get install telnetd[/FONT]
  
I'm now able to Telnet into the server from my windows pc, no stress, as well as from putty

next step : 

[FONT=&quot]install an ftp server [/FONT] : [FONT=&quot]Type apt-get install proftpd 

choose inetd installation

All good till here, [/FONT][FONT=&quot][FONT=&quot]still need to set up an account that will allow someone to upload their web pages without having access to any other parts of the system.

Next step : [/FONT][/FONT]
[FONT=&quot]Switch to the /etc directory by typing cd /etc. We need to edit the file called shells and add a new line that says /bin/false to the file. Then, when we set up a new user account for our web user, we&#8217;ll configure their account so that /bin/false is their command shell. Because there&#8217;s no such shell, they won&#8217;t be able to log in with telnet.[/FONT]
  [FONT=&quot][FONT=&quot]
[/FONT]Done

Now this where I'm not sure if I did more harm than good.........

****************************************************************
Creating a user account
****************************************************************
These where the instructions:
[/FONT]
[FONT=&quot]Let&#8217;s make an account for a user called krillin with a password of flintstone.  These are the steps that you need to do for each web user account you want to create:[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]cd /var/www
mkdir krillin
useradd krillin &#8211;p xxxx &#8211;d /var/www/krillin &#8211;s /bin/false
chown krillin krillin
passwd krillin and, when asked, choose flintstone as the password.[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]Note that xxxx above is your root password, not the one that you want to assign for the krillin account.[/FONT]
  [FONT=&quot]******************************************************************
----------------------------------------------------------------------------------------------
THIS IS WHAT I DID :

[/FONT]- [FONT=&quot][FONT=&quot]cd /var/[/FONT]
- ls -hal 

Notice no /www

- cd ..
- ls -hal

I see that the /www folder exists here, so me being me, logically, the document states [/FONT][FONT=&quot][FONT=&quot]" cd /var/www[/FONT] "

So what bright spark me goes and does is : 

- mv /www /var

- cd /var

- ls -hal

I now see that the /www dir exists

Chuffed with myself, I now :
[/FONT]
[FONT=&quot][FONT=&quot]cd /var/www
mkdir krillin
useradd krillin &#8211;p xxxx &#8211;d /var/www/krillin &#8211;s /bin/false
chown krillin krillin
passwd krillin and, when asked, choose flintstone as the password.
----------------------------------------------------------------------------------------------

So now apparently if I telnet with the new user that was created it should work......

That works, BUT also if I [/FONT][/FONT][FONT=&quot]create a simple index.html file and use ftp to upload it, using the webuser1/flintstone account.  Then surf to [/FONT][[COLOR=blue][FONT=&quot]http://192.168.1.10/krillin[/FONT][/COLOR]]("http://192.168.1.10/webuser1")[FONT=&quot] from any machine on your LAN I should see the uploaded page.[/FONT]  [FONT=&quot][FONT=&quot]

WRONG

This doesnt work and I am now stuck, having a couple of cold ones, posting this message

Any assistance would be greatly appreciated:confused::confused:

[/FONT]


[/FONT]

---

### Post by Cheesemill on 2013-02-08
Where on earth did you get the guide you are following?

It is terribly out of date and has some serious issues.

You shouldn't be installing telnetd on anything nowadays...

I would suggest using a different how-to instead, I've linked to some suitable ones below.

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp)
[http://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin](http://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin)
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by JonesK on 2013-02-08
Thx for the update, so Im going to follow one of the guides you posted, do you suggest I move the /www dir back to where it was and remove the user that I've added before starting from the beginning, or would it be best to re-install the OS?

---

