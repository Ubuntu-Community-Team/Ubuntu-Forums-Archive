---
title: "is there GUI setup for ADSL in ubuntu 9.10?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by medya on 2009-10-21
I am sorry if this question has been asked before .

I wanna know a Clean Easy Way to setup my ADSL internet in ubuntu .
in windows I make a pppoe connection and I enter my username/pass and thats it .

pleae dont tell me about *sudo ppoeconf* (I hate that terminal based app which is so buggy for me)

is there any nice way to do it graphically ?

---

### Post by martrn on 2009-10-21
Doesn't system-->administration-->network recognise your dsl modem ?

What dsl modem do you have ?

---

### Post by medya on 2009-10-21
I have a ethernet ADSL modem . it is Corecess modem .
how ppl like me, usualy set up their interent ?

---

### Post by martrn on 2009-10-21
If you are connected via Ethernet it should be fine and ubuntu should recognize the Ethernet modem when you boot up during the boot up sequence.  Its only when you connect via usb things get a lot different.

Can you enter [http://192.168.1.1](http://192.168.1.1)  and type the password (default=admin:admin) in an internet browser to view the modem initialisation process ?

Does system-->administration-->network  recognise any network devices such as point-to-point, wired, or dsl devices ?

---

### Post by bshosey on 2009-10-21
System> Preferences> Network Connections then click on the DSL Tab.

---

### Post by medya on 2009-10-21
@martrn

I dont want to enter modem config (because it is hard work to do and it causes problem with my internet I have to enter too many parameters)
in windows all I have to do is create a new connection and enter username/password .

@bshosey :
in ubuntu 9.04 the System> Preferences> Network Connections 
doesnt work, because I keep on entering the info but it goes away as I never entered it . (hope it has been solved in 9.10)

I wonder why there is no Wiki page or help page on ubuntu, for the Step By Step, ADSL config setup .

---

### Post by wojox on 2009-10-21
Open a terminal:

```
sudo pppoeconf
```

Answer the questions.

---

### Post by bshosey on 2009-10-21
I am sorry I thought you where running 9.10. Can you get to 192.168.1.254?

---

### Post by ikisham on 2009-10-21
Before I set my modem in router mode, which enables auto DHCP, I had to connect through pppoeconf. It always worked (in Intrepid and Hardy).
If you can't connect, maybe you need to stop it's process:
```
sudo poff dsl-provider
```
```
sudo pppoeconf
```

---

### Post by medya on 2009-10-21
I dont like pppoeconf, I want a modern-like tool like "windows connection"

I just say it is so wired, that in all ubuntu tutorials there is no good tutorial for ADSL internet users , we want something that looks god ! not terminal based stuff. (we want an icon in tray-icon)

---

### Post by hugmenot on 2009-10-21
I&#8217;m not kidding. I once dumped Ubuntu Intrepid onto a girl&#8217;s laptop when she was over to watch a high-res movie with me. Turned out playback on her higher powered laptop on Vista was even more choppy than on my machine. So we had no recourse but to make a spontaneous hard disk install to free the CD drive.

The next day she popped up in my IM saying how she likes this Linux and how everything is much smoother. I was baffled and asked how she got onto the internet in the first place, knowing that she had not once used Linux before and had a DSL modem. She replied, why, is this a big deal?

Somehow I found that significant because I still had things like pppoeconf in mind and wasn&#8217;t aware of how much NetworkManager makes things fool proof nowadays.

---

### Post by ranch hand on 2009-10-21
The guys from the telephone co-op here came and hooked us up for ADSL and, of course, brought a disc of drivers and some other stuff for getting Win JerryLewis Pro to hook up.

They just kind of stood there and watched as I fired the box up and was connected when the Dexktop came up.  I pulled up FF and went to their website.  Poor buggers shook their heads and said "Well, never saw anything like that before."

I don't think the OP is going to have any problems.

---

### Post by ronacc on 2009-10-22
@ ranch hand   Same here , wireless takes a small amount of set up but a wired connection either cable or adsl it just grabs at boot .mabye hes got a flaky router .

---

### Post by medya on 2009-10-22
but pppoeconf is lame, because I cant easily make two connections .
if u config it once, that would be it .

but I have two accoutns one for day and one for night (free download in the night) so each day I would have to make pppoeconf -setup to change my configuration , and sometimes I have to turn off my modem 3-4 times so pppoeconf can recogonize it .

I just need a graphical Connection Maker for Linux , if u know any tutorial or application , it would be great.

---

### Post by n0_mad on 2009-10-22
in 904 you could make dsl connection easy with network manager, but it broken in 910

---

### Post by Keyper7 on 2009-10-22
> **medya said:**
> but pppoeconf is lame, because I cant easily make two connections .
if u config it once, that would be it .

but I have two accoutns one for day and one for night (free download in the night) so each day I would have to make pppoeconf -setup to change my configuration , and sometimes I have to turn off my modem 3-4 times so pppoeconf can recogonize it .

I just need a graphical Connection Maker for Linux , if u know any tutorial or application , it would be great.

I don't get it. Why are you not satisfied with NetworkManager? I have an ADSL at home. I right-click on the NM tray icon, go to connection management, select the DSL tab, enter the server, username and password and it's done. And I can create multiple connections and switch between them seamlessly.

---

### Post by n0_mad on 2009-10-22
> **Keyper7 said:**
> I don't get it. Why are you not satisfied with NetworkManager? I have an ADSL at home. I right-click on the NM tray icon, go to connection management, select the DSL tab, enter the server, username and password and it's done. And I can create multiple connections and switch between them seamlessly.
Which version do you have 904 or 910? It worked for me in 904 but broken in 910, i ma forced to use ppoeconf.

---

### Post by Keyper7 on 2009-10-22
> **n0_mad said:**
> Which version do you have 904 or 910? It worked for me in 904 but broken in 910, i ma forced to use ppoeconf.

9.04. Which problem are you having? Did you file a bug report or checked if there's one already?

---

### Post by n0_mad on 2009-10-22
Yes there is bugreport [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/456400](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/456400) .

---

### Post by 6205 on 2009-10-22
I am not sure what is this thread about, but if you have DSL modem/router connected through ethernet, there is no need to configure anything through some gui, because all these devices have web interface and you should be able to configure it through Firefox. You need only to know IP adress of that router and default username/password login.

---

### Post by ikt on 2009-10-22
> **6205 said:**
> I am not sure what is this thread about, but if you have DSL modem/router connected through ethernet, there is no need to configure anything through some gui, because all these devices have web interface and you should be able to configure it through Firefox. You need only to know IP adress of that router and default username/password login.

The DSL tab in Network Manager is mainly for those who have ADSL Modems that connect to the PC via USB?

Every ADSL modem I've come across that connects to the PC via Ethernet requires no network manager username and password setup. (Because that's all configured on the modem itself)

---

### Post by ronacc on 2009-10-22
if I understood his last post correctly he wants two different accounts ( user names ? ) for the same connection because he needs to switch accounts at night to take advantage of free downloads . I'm not sure how you would do that , I never needed to try .

---

### Post by VMC on 2009-10-22
I'm as confused as some others are. I don't see or don't understand the question. I have a WIRED DSL connection. I didn't do anything but just boot and use the internet. Everything was automatic. I know of wireless issues, but I thought the op had a wired DSL. But then the two connections came up seemingly out of nowhere. If what is meant by two connections is to be able to have two separate computers using the internet then yes a router or hub will be sufficient. I used it all the time. My hub takes care of any collisions. 

So simple its stupid. Plug crossover cable from DSL modem into hub , plug two cables from hub into two separate computers, one being karmic and off I go.

Just for grins, heres my Wired Internet Connection.

---

### Post by Teamgeist on 2009-10-22
> **VMC said:**
> I'm as confused as some others are. I don't see or don't understand the question. I have a WIRED DSL connection. I didn't do anything but just boot and use the internet. Everything was automatic. I know of wireless issues, but I thought the op had a wired DSL. But then the two connections came up seemingly out of nowhere. If what is meant by two connections is to be able to have two separate computers using the internet then yes a router or hub will be sufficient. I used it all the time. My hub takes care of any collisions. 

So simple its stupid. Plug crossover cable from DSL modem into hub , plug two cables from hub into two separate computers, one being karmic and off I go.

Just for grins, heres my Wired Internet Connection.

Well, that how it works when you have a router and a wired connection. The router is always connected to the internet.

The DSL-tab, and that's what the threat starter refers to, is for the instances where you have a ADSL-**MODEM** and not a router, meaning you have to "dial up" to your ADSL provider everytime you switch the PC on.

Just for clarification.

---

### Post by ranch hand on 2009-10-22
Out modem, supplied by the co-op, is connected all the time unless you turn it off.  As long as it is on before you boot up, you are connected.

I have a router here but all the way across the street, the dreaded mother in law does not.  You boot up her computer, Win Jerry Lewis Pro or Ubuntu, and you are connected.

---

### Post by VMC on 2009-10-22
> **Teamgeist said:**
> The DSL-tab, and that's what the threat starter refers to, is for the instances where you have a ADSL-**MODEM** and not a router, meaning you have to "**dial up**" to your ADSL provider everytime you switch the PC on.

Just for clarification.
Are you sure about this? ADSL is not the same thing as dial-up as in the old dial-up modem.

---

### Post by hugmenot on 2009-10-22
> **VMC said:**
> Are you sure about this? ADSL is not the same thing as dial-up as in the old dial-up modem.

Yeah. God, this thread is out of control.

[PPPoE]("http://en.wikipedia.org/wiki/Pppoe") is dial-up in the sense that it uses PPP (...over Ethernet...). The DSL modem »dials« a bogus number and logs onto the remote DSLAM.

And the DSL Tab in NetworkManager is /exactly/ what the OP wants. There is no doubt about it, just go there and configure it. You can even configure multiple accounts there!

NetworkManager DSL tab == easy GUI equivalent for pppoeconf

So there. any more questions?

---

### Post by ronacc on 2009-10-22
I think what he is asking is that he has 2 different accounts that connect through the same adsl modem and he needs a way to switch between them .  With either adsl or cable being "always on " the logging in to the provider is I'm pretty sure handled by the modem itself not the OS you are running .
 question for the OP , do your 2 accounts each have a different static ip address ?

---

### Post by ranch hand on 2009-10-22
> **VMC said:**
> Are you sure about this? ADSL is not the same thing as dial-up as in the old dial-up modem.
This is an interesting thread from the PhatDebian forum on this very issue, I don't know if it would be any help to the OP but I thought you might find it informative;
[http://www.phatdebian.com/forum/viewtopic.php?f=9&t=44](http://www.phatdebian.com/forum/viewtopic.php?f=9&t=44)

---

### Post by sudoer541 on 2009-10-22
> **bshosey said:**
> System> Preferences> Network Connections then click on the DSL Tab.


Follow what this guy said. that method works for me and I tried it on 5+ modems.

---

### Post by VladimirCZ on 2009-10-22
> **sudoer541 said:**
> Follow what this guy said. that method works for me and I tried it on 5+ modems.

Hopefully that will work for you. There was a bug in the beta of Karmic and it did not work.

---

### Post by medya on 2009-10-22
look , to clarify what I mean , I want a Graphical Dailer for adsl .
somethign that I can change username / password easily and then click on Dail and make a NEW ADSL connection . then I can see the icon in the tray . thats shows it is enabeld.

---

### Post by martrn on 2009-10-22
> **6205 said:**
> I am not sure what is this thread about, but if you have DSL modem/router connected through ethernet, there is no need to configure anything through some gui, because all these devices have web interface and you should be able to configure it through Firefox. You need only to know IP adress of that router and default username/password login..

I concur with #6205, you should be able to connect directly via eithernet and set all your settings via a browser connected to the asdl/bridge/router, if its ethernet.

---

### Post by ranch hand on 2009-10-22
He has two ADSL accounts.  One for daytime use and another, cheaper one for night time use.  He needs to be able to switch from one to the other easily.  This is for reasons of cost as he pays based on his usage.

There has got to be a way to help this feller.

---

### Post by VMC on 2009-10-22
> **hugmenot said:**
> The DSL modem »dials« a bogus number and logs onto the remote DSLAM.This is in error. DSL has no "dialing" involved. Just because you use the same twisted pair don't get confused that something somewhere is "dialing" anything:

"DSL (digital subscriber line) technologies, often grouped under the term DSL, connect a computer to the Internet. DSL uses existing copper pair phone line wiring in conjunction with special hardware on the switch and user ends of the line. This special hardware allows for a **continuous** digital connection over the phone lines.

Since the connection is digital, DSL technology **doesn't have a digital-to-analog conversion like traditional modems**. It eludes voice audio spectrum frequency boundaries because it can use frequencies above the voice audio spectrum. This means you can use your phone while maintaining your Internet connection."

[**Source**]("http://kb.iu.edu/data/ajfr.html")

---

### Post by ranch hand on 2009-10-22
I think you are missing the point.  I do not think he actually wants to "dial", he wants to connect to either of two DSL accounts.  To do this he needs to disable one and enable the other.

I have not got a clue about it.

The only thing I know for sure is that his english is a lot better than my kurdish.

---

### Post by xebian on 2009-10-22
Install Kubuntu and you can find the kppp.

---

### Post by hugmenot on 2009-10-22
> **VMC said:**
> This is in error. DSL has no "dialing" involved. Just because you use the same twisted pair don't get confused that something somewhere is "dialing" anything:

"DSL (digital subscriber line) technologies, often grouped under the term DSL, connect a computer to the Internet. DSL uses existing copper pair phone line wiring in conjunction with special hardware on the switch and user ends of the line. This special hardware allows for a **continuous** digital connection over the phone lines.

Since the connection is digital, DSL technology **doesn't have a digital-to-analog conversion like traditional modems**. It eludes voice audio spectrum frequency boundaries because it can use frequencies above the voice audio spectrum. This means you can use your phone while maintaining your Internet connection."


Huh? That source has very much clueless talk (or it is grossly simplifying in laymans terms). Of course it has a digital-to-analog modulation converter. It&#8217;s a modem, right? The fact that it uses a different band on the line [doesn&#8217;t change  that]("http://en.wikipedia.org/wiki/DSL_modem#Compared_to_voiceband_modem").

And when I said in quotes that it »dials« I meant to point out that it is a PPP connection. Clumsily I admit.

Anyway, this thread is insane. Unsubscribing.

---

### Post by VladimirCZ on 2009-10-28
Making ADSL connection via Network manager DSL tab under 9.10 does not work since the Beta version. There are two main bugs related to this:

1) pppd doesn't play well with NetworkManager while establishing DSL connection [https://bugs.launchpad.net/bugs/459441]("https://bugs.launchpad.net/bugs/459441")

2) Unable to establish DSL connection [https://bugs.launchpad.net/bugs/432205]("https://bugs.launchpad.net/bugs/432205")

Until a fix is released the old method needs to be used:
sudo pppoeconf
pon dsl-provider / poff dsl-provider

---

