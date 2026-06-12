---
title: "How to install Ubuntu on Acer Aspire 3623NWXMi"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by markbear on 2006-12-14
A few weeks ago I bought an Acer Aspire 3623NWXMi laptop: I bought it specifically because the label on the box said that it came preloaded with "Linpus Linux", and I thought that it would be nice to buy a laptop with Linux preinstalled, so that I wouldn't have to go to the trouble of installing Linux and getting it running.

It turned out that the Linpus Linux installed was only a very basic Linux with command-line interface, and cannot function as the machine's operating system in any realistic sense.

When I raised this issue with Acer, their answer was that the Linux shipped with the 3620 series is not testified or qualified for use with the products, and the "Linpus boot loader" is supplied "for those that wish to install their own Linux operating system".

So clearly I will have to attempt to install Linux on my own: Ubuntu looks like an excellent candidate.

The Acer has two 20-gig partitions, one of which has the Linpux Linux, the other of which is empty.

When I start the computer, Linpus loads and I get a command line interface.

If a CD is in the CD/DVD drive, it is ignored.

I asked Acer how to get the machine to bypass the Linpus Linux and to boot from a CD: their answer was:

'Press F2 to enter BIOS Setup during Power-On Self-Test (POST while the Acer logo is being displayed).
2. Arrow over to "Boot".
3. Refer to on screen instructions to set the 1st device to "CD-ROM Drive".
4. Press the CD-ROM drive eject button and insert the CD.'

Here are my questions to the community:

(1) Is Ubuntu a reasonable choice for a Linux system on the Acer?  If not, is there another Linux distribution which would be suitable?

(2) If I load Ubuntu, should I load the Desktop version or the Alternate install version?  (My impression is that Desktop depends on there already being a Windows operating system present.  Since there is no Windows system on my machine, I suspect that I should use the Alternate version.)

(3) Should I simply ignore the Linpus Linux and install Ubuntu on the other partition?  Or does Acer's mention that Linpus is there "for those wishing to install their own Linux operating system" mean that I should somehow be using the Linpus Linux as part of setup?

(4) Do Acer's instructions for getting the machine to boot from the CD appear accurate and complete?

(5) Once the Ubuntu Linux is installed, how do I ensure that it is the operating system that the machine uses as its default from that point on?

(6) Is there anything else I should know before I start on the adventure of attempting to install Ubuntu?

Thanks to everyone in advance!  I appreciate your help.

---

### Post by lingnoi on 2006-12-15
I'll try and answer your questions the best I can.

1) It depends how well your installation goes and if you have to time to put in to fixing any problems you might have. My personal opinion is of course that Ubuntu is probably the easiest Linux distribution to get up and running.

2) You should use the Desktop version. If you want to use KDE (a window manager that has a user interface like windows) then use Kbuntu. If you want to use Gnome (a user interface more like mac) then choose the Ubuntu disk.

3) If you're not going to use it then you can install over it if you want. Just delete the partition before you install Ubuntu. You don't have to though.

4) Seems fine. If you need extra help then reply and I'm sure someone will help you.

5) There is a menu select screen call Grub that lets you select which operating system you want to boot when you turn on your laptop.

6) You probably will have some problems and the more your comitted to fixing the problems that arise then the more you will learn. If you come up with the attitude that "its not working, just want it to work" then you probably won't get very far.

The wiki and forums are the best places for information and finding out problems.

Here is my thread on problems you might get with your laptop and how to fix them.

[http://www.ubuntuforums.org/showthread.php?t=295942]("http://www.ubuntuforums.org/showthread.php?t=295942")

I hope this helps. :D

---

### Post by Herman on 2006-12-15
Hello makrbear,
> (1) Is Ubuntu a reasonable choice for a Linux system on the Acer? If not, is there another Linux distribution which would be suitable? Ubuntu is a great choice. We have two Acer laptops and four Acer Desktops in this house and they all have Ubuntu installed and working well. 
> (2) If I load Ubuntu, should I load the Desktop version or the Alternate install version? (My impression is that Desktop depends on there already being a Windows operating system present. Since there is no Windows system on my machine, I suspect that I should use the Alternate version.) The 'Desktop' CD has a Live operating system so you can try Ubuntu out first and make sure it suits your hardware before you decide to install. The Live operating system can also come in handy after your install for several kinds of special jobs you might want to do to your installed system at some time or another. If you decide to install, here's the best website to read up on how to do that, [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
It doesn't matter if you have Windows installed or not, but if you are going to get Windows, it's does make things a little easier if Windows is installed first, then Ubuntu. However, it can be done the other way around with only a little more effort. 
The 'Alternate' CD offers more choices and options, and can be used to do special installations, for example it can install in machine with very little RAM, install the bootloader anywhere you like and that sort of thing. Click my first sig link to see what an 'Alternate' CD install will be like.
> (3) Should I simply ignore the Linpus Linux and install Ubuntu on the other partition? Or does Acer's mention that Linpus is there "for those wishing to install their own Linux operating system" mean that I should somehow be using the Linpus Linux as part of setup? I have never heard of it before. I'd keep it just for fun, but you won't need it for anything. I am curious about what it's like, but we already have the Grub bootloader. It's hard to imagine any other bootloader being as good as Grub. I would just leave linpus there ofr now, it won't do any harm, except it's taking a lot of your hard disk space.
>  (4) Do Acer's instructions for getting the machine to boot from the CD appear accurate and complete?
Well with mine it's the 'Delete' key, but those instructions look reasonable, but a little brief. It isn't very difficult, you'll be able to figure it out. It'll be something like this, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").
> (5) Once the Ubuntu Linux is installed, how do I ensure that it is the operating system that the machine uses as its default from that point on? It will be automatically set up that way in Grub.
>  (6) Is there anything else I should know before I start on the adventure of attempting to install Ubuntu?


---

### Post by markbear on 2007-01-20
Thank you to both Lingnoi and Herman for your prompt and very helpful replies.  I've made enough progress that I can now report back, both as a thank you to yourselves and in order to assist others who find themselves in a situation similar to mine.

The answer from Acer technical support on how to boot from the CD drive turned out to be entirely correct, so I was off to a good start.

LIVE CDs
My approach was thorough: knowing that laptops, with their specialized hardware and firmware, are tricky to deal with, I created Live CDs for all four versions of Ubuntu: Ubuntu proper, Edubuntu, Kubuntu, and Xubuntu.

UBUNTU AND EDUBUNTU
During the loading of the Live CDs, I received an error message saying that there was a hardware conflict with Gnome.  In both cases, the Live CD continued to load, but it was obvious that there really was a problem: system performance was slow and unstable.

I tried a permanent install of Ubuntu, and got the same message, which was reassuring, because it suggests that system behaviour during the load of the Live CD predicts very accurately the behaviour of a permanently installed system.

KUBUNTU
Kubuntu's Live CD had no issues at all, and installation was smooth.

Kubuntu is indeed quite intuitive for someone used to Windows: in fact, even the shortcut keys are quite similar.  Where there is a difference, I preferred the austere elegance of Kubuntu to the complexity of Windows.

The Kubuntu Live CD included most of Open Office, which I was used to with Windows.  It works exactly the same way, so there was no learning curve.

The CD burning software was extremely well designed, and seems to be very reliable.

The Kate editor was a pleasure to use when editing plain text files.

XUBUNTU
As with Kubuntu, there were no issues either with using the Live CD or with actual installation.

Xubuntu is meant for computers that are small or slow.  The Acer is fairly large and runs quite fast.  What this meant was that Xubuntu and its applications run unbelievably fast.  I have never seen a pdf document or jpeg load as fast anywhere else.  Similarly, the Abiword word processor comes up instantaneously: there is no lag while the window is displayed and gradually filled.

It was a pleasant discovery to find that the Gimp image editor program was included.

Xubuntu comes with the Firefox browser and Thunderbird for email, both of which I use on my Windows machine.  Because of this and because of Xubuntu's speed, at whatever time I achieve Internet connectivity (the remaining challenge), it would become my environment of choice for day-to-day computer use.

CURRENT CONFIGURATION
Installing any version of Ubuntu involves telling the installation program which partitions to use.  I haven't done such low-level work as partitioning since I retired my Amiga, but the part of the installer that did the partitioning was about as intuitive and reliable as it could possibly be.

In the end, I removed the Linpus distribution which Acer had shipped with the machine.  I could not see that it offered anything not also offered by Kubuntu and Xubuntu, both of which have very nice command-line interfaces.  So I've given 20GB to each of the two.  There were one or two mentions on the Ubuntu websites to the effect that it is possible to have more than one desktop environment in the same partition, sharing the same underlying Ubuntu base, but it appeared that this involved getting a component from the internet, and internet connectivity is the one remaining issue.

Getting both versions installed in their separate partitions took a few tries, but things worked out, and the experimentation was useful in that it gave me experience in working with the partition manager.

CURRENT STATUS
Kubuntu and Xubuntu are functioning flawlessly.  They come with quite different application programs, so I make use of both environments.

On the basis of my experience so far, I would say that Linux definitely lives up to its reputation.  It's reliable, very easy to use, and I have the feeling, which I haven't had for some years, that my computer belongs to me, not to the company that made the operating system.  But there is one final step that I have not been able to make.

THE LAST STEP: INTERNET CONNECTIVITY
I live in Canada, and have a dial-up Internet account.  (This is not really much of a constraint for most of what I do, since my ISP is reliable, and I really do get a predictable speed of 56K whenever I'm on the net. A friend with high speed helps when a larger download is needed, such as the Live CDs)

The one remaining issue is that it is not at all clear how I should go about setting up the internet connection.  I'll investigate further and post questions on the forum if necessary.  I've gotten further with Xubuntu than Kubuntu, but am still getting a message incorrectly stating that the modem is busy.

Really, this is the only area where Xubuntu/Kubuntu fall short of Windows, which has a remarkably straightforward process for setting up connectivity.

SUMMARY
My Acer is no longer a paperweight, but an actively used standalone machine with interesting and very useful programs.  My thanks to both of you for your help, and my best wishes to anyone reading this post who is embarking on the installation of Ubuntu on a laptop.

---

