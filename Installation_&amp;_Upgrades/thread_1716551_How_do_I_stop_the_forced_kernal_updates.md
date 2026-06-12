---
title: "How do I stop the forced kernal updates?"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by ashleycrue123 on 2011-03-28
Several months ago I asked a question concerning kernal updates that caused a problem. It was thought that a later or newer kernal would fix the problem which is has not.

So to save myself the waste of time each time a kernal update comes through and having to go back to one that works, I would like to be able to prevent the constant alerts from the update thing to install them.

I know to deselect them but each time I turn this laptop on I get alerted to the updates. 

Please don't lecture or reply saying the updates are needed because they cause this laptop to cease working and everything has been tried. All I want is to be able to permanently turn kernal updates off.

Many thanks in advance to anyone who can help.

---

### Post by 23dornot23d on 2011-03-28
In your System Menu go to 

Preferences - Startup applications - ( then untick - Update Notifier )

It turns off all updates ...... being shown at startup .... but you can always do the updates


manually like this ............ ( I still use this method ....  ) 

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude safe-upgrade

( along list of updates may come up then ........ just cut and paste everything but the kenel updates after the following line )

sudo aptitude install

---

### Post by CharlesA on 2011-03-28
> **23dornot23d said:**
> In your System Menu go to 

Preferences - Startup applications - ( then untick - Update Notifier )
That will disable any update notifications.

@OP: You might want to check here:
[http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)

---

### Post by 23dornot23d on 2011-03-28
Ok ty I did not realise that existed ...... sorry ignore what I said :confused:

---

### Post by ashleycrue123 on 2011-03-29
> **CharlesA said:**
> That will disable any update notifications.

@OP: You might want to check here:
[http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)


Thankyou to both of you.

I had tried the first piece of advice before asking. And the link provided in the second reply was exactly what I wanted. Cannot thankyou enough. I didn't know about it. 

I've now booked marked the site as it seems to have alot of useful stuff.

---

