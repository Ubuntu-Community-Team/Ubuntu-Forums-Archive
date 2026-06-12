---
title: "Help!!!! Java applette  stops working"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by perro68 on 2010-06-15
WHat would cause an applette to stop working after performing an upgrade?

there is one applette that would allow me to access a site that just stoped workign when i upgraded the distrubution

how can i determine exactly what caused this

---

### Post by Mr_Bumpy on 2010-06-15
It's possibly because Ubuntu 10.04 uses openjdk rather than sun-java6 for its Java runtime.  You can change it back by following these steps:
1. Make sure the Lucid partner repository is enabled (go into System -> Administration -> Software Sources, and on the second tab, make sure the box next to "http://archive.canonical.com/ubuntu lucid partner" is checked)
2. Paste the following commands into a terminal:
```
sudo apt-get remove icedtea6-plugin
sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-fonts sun-java6-jdk
sudo apt-get remove icedtea-6-jre-cacao openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
```
3. Set the Sun JDK as your default Java installation:
```
sudo update-java-alternatives --set java-6-sun
```
4. Test:
```
java -version
```

Hopefully that will fix your broken Java applet.

---

### Post by perro68 on 2010-06-16
This does not seem to work

i have no idea where to begin diagnosing the error

like i said it works fine....on 9.04

but once i upgrade the site gives me a login error


it uses a java applet to log in with


I looked up the error itself on a separate website


[FONT=Arial][SIZE=3] Problem:  Unable to access DTS (Error  message "There has been a problem with Login.  Problem getting security  information from your computer.  Please contact your DTS site administrator for  assistance."), or DTS stalls at DBsign:  logging into cryptographic libraries....

[/SIZE][/FONT][FONT=Arial][SIZE=3]**Cure** :  In Internet Explorer:  [/SIZE][/FONT][FONT=Arial][SIZE=3]Go to Tools, Internet  Options, Security (tab), Click on Trusted Sites (green checkmark), Click Sites  (button), in the Add this website to the zone:   type in  "****.osd.mil***" after unchecking "Require Server Verification", click  add (button), select close, then click OK
[/SIZE][/FONT]**[FONT=Arial][SIZE=3]Cure2:  Go to:  Tools, Internet  Options, Security (tab), click on the Internet Security option.  Uncheck the box  for Enable Protected Mode.  [/SIZE][/FONT]**



question how does one add a trusted site in Firefox ....is does not handle security the same as IE

could it be setting of firefox that keep me from loging in

again

it works fine on 9.04 ....i format the drive install 9.04 ...i install everything

and it works fine ...but when i upgrade .... i get the log in error

I would hate to go back to windows ..... and i would not want to have use 9.04 when 10.04 is available of date
[FONT=Arial][SIZE=3]
[/SIZE][/FONT][FONT=Arial][SIZE=3]   

[/SIZE][/FONT]

---

### Post by darkod on 2010-06-16
Have you tried clean install of 10.04?

Why install 9.04 and do two upgrades to reach 10.04. Maybe the upgrades are getting something wrong.

Did you make sure you are using sun jdk as the previous reply suggested? When you check the version does it say sun jdk?

---

### Post by perro68 on 2010-06-17
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)


this is what i get when i do the version commant

i am at a lost with this


what could be the sourse of my issue


i still can not log in ....

i did a str8 install with a 10.04 disk .....i get the same error

---

### Post by perro68 on 2010-06-18
I have tried a clean install of Lucid and logging in gives me the same error as mention above

I have 9.04 jaunty installed on a partition now and it works fine.......perfect

how can i lock my firefox and java and still upgrade my distrubution



On the 10.04 partition i cleaned out every reference of java i could find ....reinstalled

and it still did not work

SOMEONE PLEASE HELL ME

---

### Post by darkod on 2010-06-18
Can you ask for support from the website you are trying to log into? I am using Lucid and still haven't found a single website that would refuse to log me in.

Sometimes they design websites around IE and they are not even aware of issues that can come up in Firefox. Maybe it's affecting Firefox 3.6 only, I don't know.

---

### Post by perro68 on 2010-06-18
> **darkod said:**
> Can you ask for support from the website you are trying to log into? I am using Lucid and still haven't found a single website that would refuse to log me in.

Sometimes they design websites around IE and they are not even aware of issues that can come up in Firefox. Maybe it's affecting Firefox 3.6 only, I don't know.

I am using firefox 3.6.3 on jaunty ...it works fine

it is when i urgrade to karmic it stops working

a clean install of lucid does not work either 


is there a way i can lock everything in place so to speak as far as java and firefox is concerned and still upgrade to karmic and than lucid?


i

---

### Post by kyyp912 on 2010-08-15
Ubuntu 10.04 can be used to sign into DTS using the following out of the Software Center:

**OpenJDK Java 6 Runtime** - This along with the Web Start are the JRE equivalents

**OpenJDK Java 6 Web Start** - This along with the Runtime are the JRE equivalents

**Icedtea Java Plugin** - This is the Firefox plugin to allow JRE to run

**Smart Card PKCS #11 cryptographic module** - Permits use of the CAC Reader. Must have the Key applet

**Smart Card Cool Key applet** - Permits use of the CAC reader.  Must have the crypto module

These along with the set up to permit FireFox to use the CAC will allow you to get into the DBsign portion of the DTS login.  *Unfortunately*, I don't know what to put in for the set up of DBSign to actually get into my login.  I cannot locate my certs though it. If anyone gets past this portion, please update.  

Kyyp

---

### Post by JT3 on 2010-08-30
Have you had any luck yet?  I am in a similar boat.  CAC card works for other sites but here I keep getting the DTS login error and it never asks for my pin.
**Login Error**                            **There has been a problem with login**      
The site is experiencing technical difficulties.  Please try again later or contact your DTS site administrator for assistance. 



Thanks!

---

### Post by ta1kradio on 2010-09-12
Same issue here. Any luck resolving?

---

### Post by daniel.cotter on 2011-03-12
Ok,  I am reading through this, because I can get past the DBSign portion, but it just sits there telling me "Signed Successfully..."  then does not load the page.  I am going to try some of what has been suggested, and I will let you know if anything works.  (10.10 user)

---

### Post by daniel.cotter on 2011-03-12
Ok,

I know this thread is a couple months old, but the issue is new to me, and I did not find the answer on this forum, so maybe it is still an open issue for some of you.

I found a solution [here]("http://zxq9.com/dodcac/U10.4-LTS-32/Ubuntu10.4-LTS-32.html#Java").

It speaks of 9.04, but it worked for me, and I am running 10.10.  It deals with the DoD site's applet (DBSign) being written for the Sun version of the JDK.

The instructions there worked beautifully, and I can log into DTS now.

---

### Post by mccartyj on 2011-11-10
Has anyone gotten this to work in 11.10?

I had it working in 10.04, but had to switch to CACKey vs CoolKey when I upgraded to 11.10...

From the looks of it, the DBSign suite does not communicate at all with the CAC card when it asks for a password. It works fine (and lights up) on other sites like OWA and AF Portal...

---

