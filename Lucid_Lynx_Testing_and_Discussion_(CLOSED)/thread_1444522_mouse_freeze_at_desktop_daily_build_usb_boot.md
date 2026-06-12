---
title: "mouse freeze at desktop daily build usb boot"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2010-04-01
Been having this issue for the last few weeks using the 386 daily build on an ASUS p4s800d-x mobo....desktop comes up from a usb boot but the mouse immediately freezes...this machine runs 9.10 without a problem.  I have also booted OpenSolaris from a LiveCD...2009.06...and that runs fine...so I believe my hardware is OK...

Any ideas..what should I try to fix this?

thanx
rt

---

### Post by Roosje on 2010-04-02
Hi,

Little info to get a real clue, but here is what helped me with my mouse troubles (not so much a freeze, but strange focus problems) maybe it is of some use to you..
I have a Logitec mouse, it was plugged in on a powered usb hub, that has never been any trouble. Then the weirdness started, and i finally reinstalled system,  only to run into the same horror :-( After the simple switch of the usb cable directly to the computer in stead of the hub, the whole thing works like a charm again. Maybe it is of some use to you.

---

### Post by rtalcott on 2010-04-02
Thank you for the reply.  My Logitech is plugged directly in the usb port on the motherboard...I also tried a ps2 mouse and had the same freeze...I do not know how to get any more information because it freezes as soon as the desktop shows up...I suppose I should get to the command line and see if there is anything I can find...

The hardware still runs 9.10 from the drive...
rt

---

### Post by Roosje on 2010-04-03
Ok, that sounds like a lot more trouble :-( Does the system respond to keyboard presses? Another wild idea (i use it when i screwed things up to much) i delete both .gnome2 & .gnome2_private and reboot, helped me when i had upgraded from 9.10 to 10.04 and all went weird. Have you tried to google mouse freeze + ubuntu? Maybe someone out there already fixed it ;-)

---

### Post by rtalcott on 2010-04-03
It gets stranger....I connected the mouse to a front panel usb port and it worked!  I installed 10.04....yesterday's daily build...I'm thinking GREAT!  Well....I try to get on the internet...can't...I see I have an IPv6 address but no IPv4...I go into network manager and it's set for dhcp...and ignore IPv6...tried to reinstall 9.10 and I get grub_rescue upon reboot...at this point I gave up...will boot the OpenSolaris LiveCD as a sanity check this morning...

I appreciate your reply!
rt

---

### Post by Roosje on 2010-04-03
No problem, i understand the frustration, atm my lucid behaves like a nice little kitten, but there have been some very unpleasant hissy-fits from the Lynx ;-)
I think that you should maybe check your system with other os options to see if it is a hardware problem. Otherwise maybe skip the beta and join again when it is released.
On my system it is just one of a multitude, so i can always fall back on Karmic, Jaunty or Fedora, or Suze, and even (shudder) XP (for the rare program i use that can or will not run on linux that i can not find a replacement for)

Good luck from Holland ;-)

---

### Post by rtalcott on 2010-04-03
I did a few more things and I was wrong...the machine does get an IP IPv4...but I cannot ping any other machine on the LAN...very strange because it receives the IP from a Linksys wrt54g router which passes along my ISP's dns IP's....that is all there BUT I cannot ping anything....I did install OpenSolaris 2009.06 and it worked perfectly....no trouble with anything so i don't think it is hardware although I could be wrong...I am very confused.  Like you I have a number of other machines....4 running Lynx and 2 running Karmic....this is just a very irritating situation...being unemployed I have LOTS (too much) time to work on this.

Very strange that I have the IP from the router AND the dns IP's but I cannot use the network.

You are quite right...time for a beer!

Thank you!
rt

---

