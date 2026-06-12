---
title: "Still major problems in Hardy"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-07-11
I think there are still too many major problems in Hardy to use it.  And this is even at the 8.04.1 revision.

I tried to get a computer I am setting up to work on a dialup account on Hardy and the system would connect using gnome-ppp on the very initial/first try and I could surf the net just fine. 

But all subsequent attempt to connect and surf the net were met with the "Firefox running in offline mode" message.  According to what I can see, I think the computer is connecting to the ISP just fine but something in Hardy, perhaps a flaw in Firefox, is preventing the use of the internet.

However, strangely enough, I can put the ("older" & I would think not as improved) Gutsy version of Ubuntu on the machine and the computer dials up to the ISP and I can surf the net EVERY time without fail.

Somebody really needs to fix this sort of thing FAST.  I really believe that stuff like this is an embarrassment to Ubuntu (I know that stuff like this keeps me from recommending Ubuntu more than I do).

And I am not looking for some juryrig workaround fix for this.  I want an O/S that I can use.  I don't want to be in the business of spending all of my time fixing it.

And yes, I have reported this as a bug.

Thanks.

---

### Post by tuxxy on 2008-07-11
> I don't want to be in the business of spending all of my time fixing it.

Wouldn't you be in this business of spending your time waiting if your on dialup anyway?

---

### Post by wpshooter on 2008-07-11
> **tuxxy said:**
> Wouldn't you be in this business of spending your time waiting if your on dialup anyway?

No, I would not, because first of all this machine is for someone else's use and unfortunately the only access they have is dialup, so yes, I suppose they will have to be doing some waiting but all of that does nothing to resolve this/these issues.

Thanks.

---

### Post by stchman on 2008-07-11
> **wpshooter said:**
> I think there are still too many major problems in Hardy to use it.  And this is even at the 8.04.1 revision.

I tried to get a computer I am setting up to work on a dialup account on Hardy and the system would connect using gnome-ppp on the very initial/first try and I could surf the net just fine. 

But all subsequent attempt to connect and surf the net were met with the "Firefox running in offline mode" message.  According to what I can see, I think the computer is connecting to the ISP just fine but something in Hardy, perhaps a flaw in Firefox, is preventing the use of the internet.

However, strangely enough, I can put the ("older" & I would think not as improved) Gutsy version of Ubuntu on the machine and the computer dials up to the ISP and I can surf the net EVERY time without fail.

Somebody really needs to fix this sort of thing FAST.  I really believe that stuff like this is an embarrassment to Ubuntu (I know that stuff like this keeps me from recommending Ubuntu more than I do).

And I am not looking for some juryrig workaround fix for this.  I want an O/S that I can use.  I don't want to be in the business of spending all of my time fixing it.

And yes, I have reported this as a bug.

Thanks.

My recommendation is to use Gutsy if it does what you want to.

The only thing I can think of is that in the new distro they did not spend much time on the dialup portion as an overwhelming majority are on high speed.

What kind of a modem does this PC have?  If it is a winmodem it is possible the new kernel does not have the proper drivers.  Winmodems are very hit or miss in Linux.  If you must dialup then get a true hardware modem.  Modems that hook up to a serial port are hardware modems.

---

### Post by Gorlith on 2008-07-11
There was a thread somewhere about firefox going into offline mode for people, i think they had a fix.

---

### Post by Vorian Grey on 2008-07-11
> **wpshooter said:**
> 
I tried to get a computer I am setting up to work on a dialup account on Hardy and the system would connect using gnome-ppp on the very initial/first try and I could surf the net just fine. 

But all subsequent attempt to connect and surf the net were met with the "Firefox running in offline mode" message.  According to what I can see, I think the computer is connecting to the ISP just fine but something in Hardy, perhaps a flaw in Firefox, is preventing the use of the internet.


It's probably the network manager. I had problems with Firefox starting in offline mode using dialup, so I went to Admim > Network and configured the network even though I do not have a network and since then FF has worked fine. Does your network manager in the system track hace a red X on it?

---

### Post by wpshooter on 2008-07-11
> **stchman said:**
> My recommendation is to use Gutsy if it does what you want to.

The only thing I can think of is that in the new distro they did not spend much time on the dialup portion as an overwhelming majority are on high speed.

What kind of a modem does this PC have?  If it is a winmodem it is possible the new kernel does not have the proper drivers.  Winmodems are very hit or miss in Linux.  If you must dialup then get a true hardware modem.  Modems that hook up to a serial port are hardware modems.

It IS an external serial port modem.

Thanks.

---

### Post by wpshooter on 2008-07-11
> **Gorlith said:**
> There was a thread somewhere about firefox going into offline mode for people, i think they had a fix.

Yes, I believe that I found and read that already.

But that is just some type of juryrig workaround, I don't think it should be referred to as a fix.

Thanks.

---

### Post by wpshooter on 2008-07-11
> **Vorian Grey said:**
> It's probably the network manager. I had problems with Firefox starting in offline mode using dialup, so I went to Admim > Network and configured the network even though I do not have a network and since then FF has worked fine. Does your network manager in the system track hace a red X on it?

Yes, it does have a red X on it but I believe that is because I have my ethernet wire disconnected from the DSL connection that I used to install the O/S and updates on the computer.  And it is disconnected because this computer is ultimately NOT going to be used on DSL but on a strictly dialup connection basis.  If I shutdown and unplug the dialup connection and go back to the ethernet/DSL, everything works fine but this does NOTHING to fix the problem with the dialup and Firefox browser not working.

And like I said, I have none of these problems if I have Gutsy installed instead of Hardy.  But I would prefer to have this work properly under Hardy, so the person that is going to wind up with this computer will have the advantages of the LTS version.

Thanks.

---

### Post by Vorian Grey on 2008-07-11
> **wpshooter said:**
> Yes, it does have a red X on it but I believe that is because I have my ethernet wire disconnected from the DSL connection that I used to install the O/S and updates on the computer.  And it is disconnected because this computer is ultimately NOT going to be used on DSL but on a strictly dialup connection basis.  If I shutdown and unplug the dialup connection and go back to the ethernet/DSL, everything works fine but this does NOTHING to fix the problem with the dialup and Firefox browser not working.


I have my network disconnected and I only use dialup. I fixed the issue by going into the network settings and choosing automatic conection (DHCP) even though I am not on a network. This allows the network to run in the background and allows FF to run in online mode even though I am not on a network. 

If you want a solution that helps FF run online without configuring the network I can't help you. I did read somewhere that you could uninstall the network manager and FF would work properly. Please research that before you do anything, because I am not positive about that.

---

