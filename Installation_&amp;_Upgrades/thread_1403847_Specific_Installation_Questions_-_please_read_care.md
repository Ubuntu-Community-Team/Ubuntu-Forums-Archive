---
title: "Specific Installation Questions - please read carefully before replying"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Doc Holliday 1128 on 2010-02-10
Hello all!  I apologize in advance for the length of the following post and am grateful to anyone who takes the time to read it.  The following is a compendium of questions that arose during several attempted installs of Ubuntu 9.1.  After searching various communities and forums without much luck I decided to post here.  I have numbered each section and tried to keep the questions relevant to the section as a whole so that you are able to number your responses.  This is to: 

a) Help encourage my understanding of your responses that may only pertain to a particular question.
b) Help prevent response repetition.
c) Promote the your elaboration upon the comments of other users.

If any of my questions have already been answered somewhere else on the web that I missed, posting a link would be greatly appreciated.  I welcome explanations from any level of knowledge and I encourage you to explain in the way it makes sense to you.  If I don't understand something, I have no problem asking for clarification.


When attempting to install Ubuntu 9.1 to dual boot with Win7, I was able to boot from disc, choose my language, and select Install Ubuntu.  At this point, my computer goes to a blank screen with a cursor flashing indefinitely.  The drive works to boot Acronis, Win7 install, and various other discs.  I've tried adjusting the boot settings in the Ubuntu menu, re-downloading and burning several copies of the Live Disc using different burning software (all at 8x speed), checking the MD5SUM, using the alternate version, and using the text based version.  Everything I've done produces the same result.  The only answer anyone seems to give is to defragment the hard drive (which I also did) and if that fails, to completely format the hard drive and start from scratch.  I'm fine with that but I had a few questions regarding the best way to do this.

1.  I've already completed a full backup by making a recovery disc and a system image file of Win7.  I need to re-size my partition for Ubuntu and was wondering if I should use the Win7 partition creator when reinstalling Win7?  Or should I use the "Try Ubuntu without any change to your computer" boot option and run Gparted from within Ubuntu prior to installing Win7?  Or should I use a Gparted boot disc to wipe and setup partitions prior to anything else?  If anyone has other ideas that make more sense I'm all ears.  Keep in mind the possibility of a fragmented (even after 4 defrags) hard drive is what might be causing my problem, thus restoring my Win7 backup _**prior**_ to installing Ubuntu is what I'm trying to avoid (pending an answer to question 2).

2.  The following is more related to Windows but I imagine there are one or two of you who have a dual boot setup.  When reinstalling Win7, I was planning on using the install disc and completing a clean install of Win7 without restoring my backup just yet.  At this point, I would then install Ubuntu.  After that, I'll be going back into Windows backup and recovery section.  From here, I believe there's an option to restore a system image from another HDD.  

[SIZE=3]_**BUT**_[/SIZE]

If fragmentation was an issue with the previous attempt to install, then it seems I should wait until Ubuntu is installed to do my Win7 recovery right?  Or instead of restoring the fragmented version onto the _**now smaller**_ partition, does all of that data get re-written and organized during that process, making my concerns about restoring Win7 before Ubuntu unfounded?  Furthermore, will restoring the disc image to a partition that is a _**different size**_ than it was when the image was created be a problem?  I just wanted to ask since I stopped making assumptions that involve computers a long time ago. Btw, I was only using 20% of the drive's capacity so this is more of a compatibility and organization question than a space question.

3.  My intention is to make my Win7 partition, a 12-20GB partition for \Root, 4GB for \Swap, and around 40-??GB for \Home.  I've read a lot of conflicting viewpoints regarding the sizes of these partitions.  Many of which say that 20GB is overkill and that 12GB is more than enough space for \root because \Home is where anything I install or save will be stored and \root only contains core system files (I assume this is why upgrading Ubuntu is so easy with 3 partitions).  Another thought is that making the \Swap partition the full size of your RAM is no longer necessary when one has 4 or more GB.  I'm wondering if someone might be able to provide me with a definitive answer on both of the above arguments as well as a brief explanation between the difference between the \root and \home if it seems like I don't quite have it right.  I would also like to hear some recommendations for the size of the data (\Home?) partition should be.  Win7 will be used solely for gaming whereas Ubuntu will be used primarily for Java but I'm a big fan of extensions and addons so I would like to err on the side of caution.  Once a partition for Ubuntu is created, can it be edited in GParted without a reinstall or corrupting data on that partition?  

4.  Lastly, I've read a few opposing viewpoints discussing 32-bit vs 64-bit.  However, none of what I've read offers much evidence for or against either one, nor does any of it seem to point out significant differences between the two.  The only thing I've seen are some complaints regarding software compatibility with 64-bit, while others refute those claims by saying nearly everything is available in 64-bit or will be very soon due to the obviously growing popularity of 64-bit systems.  Can anyone help me understand or point me in the right direction of some objective information pertaining to the 32-bit vs 64-bit idea?  I don't really know what I intend to do with Ubuntu in the long run but in addition to Java, I plan on using Ubuntu specifically as a powerful learning tool as a computer science student.  In that sense, I want to ensure I choose the one that offers the most power, versatility, and room to evolve with my needs.

I'm happy to provide any additional info or clarification that may help.

Computer Specs For Reference:

CPU - Core 2 Quad Q9400 @ 2.66 GHz
GPU - 285 GTX
RAM - 4GB DDR2
OS - Windows 7 Professional x64

---

