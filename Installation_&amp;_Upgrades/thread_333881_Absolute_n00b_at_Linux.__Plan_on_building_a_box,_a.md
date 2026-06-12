---
title: "Absolute n00b at Linux.  Plan on building a box, and using SATA.  Got questions..."
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by steven_mckenz on 2007-01-08
Hello!

So, being an absolute know-nothing regarding linux and Ubuntu, I have decided to build myself a cheap server-box to use to store my media collection, and also to be able to teach myself linux in the process.  The system will end up being around $200.00 when it is completed, and should do for what I want it to do.

However, I have never dealt with SATA before.  And while pricing out my box tonight, I have found a SATA II drive from Best Buy, 160GB, that seems to be the cheapest price/size ration that I have found so far.  I figured it would be my best bet for what I would want.

Then I found this motherboard to go with my processor.  Yes, I understand it's cheap, but all I want is something simple, since I won't be using this for anything other than storage and learning, and I don't have a lot of money:

[http://www.newegg.com/Product/Product.asp?Item=N82E16813186092](http://www.newegg.com/Product/Product.asp?Item=N82E16813186092)

So, my main question is, how much configuring will it take to get Ubuntu to install/boot on a SATA drive, rather than a standard, old-fasioned PATA drive?  I don't know much about them, nor what configurations it takes in order to get one to work properly, and have it be detected.  And since I know very little about linux, I don't know if that will take a lot of extra tweaking to get to work.  And as for me who knows nothing about it, I want to do as little tweaking as possible!

Thanks a bunch for the help, and once I get this thing bought, I have a feeling that I'll be spending a bunch more time here!

---

### Post by hal10000 on 2007-01-08
I could not find any informations about linux compatibility for this mainboard.

Have you already bought it????

if not, then you may take a look at [http://www.linuxquestions.org/hcl/]("http://www.linuxquestions.org/hcl/")
Here you can find many informations about linux compatible hardware.

I suggest a MSI K8N Neo4-F Mainboard, the price is the same as yours and it is completely compatible with linux.
I have it running with an Athlon 64 3200+ cpu (but it has no internal graphic chip). Take in mind that there are two releases of this board, one with SATA 1 and one with SATA 2.

You may find many bords with a similar price at th link above.

Have fun

---

### Post by dabl on 2007-01-08
I recently built a new system with Kubuntu in mind, and here's the SATA-relevant lesson:  Don't mix an IDE/PATA drive and a SATA drive in the same system, and plan to control where the Grub bootloader gets installed.  In that situation, it WILL go on the IDE drive!  But if you plan to have only the SATA drive, my experience indicates you should have no difficulty in that regard.

I noted that the user reviews on that cheapie mobo are not terribly inspiring -- hopefully you know what you're doing and can get it together with minimal instructions ....

;)

---

### Post by steven_mckenz on 2007-01-08
Well, so I've done a bit more looking, but I still haven't really come across any information that I find very relevant to the topic.  Thank you, to the two of you who replied though.

I took a look at the recommended motherboard.  Unfortunately, it was about 25$ more expensive, and out of stock (not including having to buy a video card for it as well).  I would really like to make the Foxconn MB work that I specified, but I know very little about SATA, and I don't know how compatible it is with Ubuntu Linux, and how much customization is required to make it work.

To the second person to reply, I don't plan on mixing and matching SATA and PATA drives together.  I'd just like to get the single SATA drive, and that would be it.  

So, my main question still, is if there is much configuration needed to make a SATA drive work in the newest version of Ubuntu (6.10).  Or will it be a simple install and load, just as if I was using a PATA as Mastor on the Primary IDE controller.

Thanks again for your help!

---

### Post by Alabaster on 2007-01-08
Also a n00b...

but one that has installed ubuntu edgy on an SATA II drive. It went smoothly, and everything Just Worked (as it should).

Watch out for the motherboard tho. My one is a brand spanking new ASUS and edgy installed all the right drivers  straight off the bat (thats incredible:cool: ). I imagine an old cheapy would be more difficult to configure.

Good luck!

---

### Post by hscottyh on 2007-01-09
That Foxxconn mobo has SIS graphics, so there is no way to get 3d accelerated graphics with it.

---

### Post by steven_mckenz on 2007-01-09
> **hscottyh said:**
> That Foxxconn mobo has SIS graphics, so there is no way to get 3d accelerated graphics with it.

That's not really a big deal to me.  I don't plan on playing any games or anything witth the computer (that's what my desktop is for!).  I just wanted the onboard video because it was cheap, and would do for me what I needed it to do.

---

### Post by hal10000 on 2007-01-09
SATA is usually very easy with linux (you don't need to configure anything).
But to avoid problems and get everthing to work I suggest you look for mainboards (with a similar price) and copmapre them with the harware compatibility list.

---

### Post by clownius on 2007-01-09
I had absolutely no problems installing Ubuntu on a SATA drive.  It is an issue when you have one SATA and one PATA drive but just the 1 SATA drive should be all smiles.  With the old cheap mobo factor i generally find its not such a factor, its the new expensive mobo's that cause the most problems lol. If you have any issues post away but if it isn't listed as incompatible id guess from my experience it generally works unless its new enough it hasn't been listed as incompatible if it is.

---

