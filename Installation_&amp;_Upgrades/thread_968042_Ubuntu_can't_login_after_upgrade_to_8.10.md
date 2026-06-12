---
title: "Ubuntu can't login after upgrade to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by CFIL on 2008-11-02
HI ALL, 

I was happy during upgrading my ubuntu 8.04 to 8.10, the upgrade complete successfully and after restart my pc it boot correctly but I can not login to the ubuntu desktop and its stop on The login screen because I choose to login automatically with my name and the screen just hangs without any thing.  just a brown background with my mouse pointer. the system won't do anything:confused:. I try to login to the shell and I did that, and then I executed the 
sudo /etc/init.d/gdm restart
and its again it comes with brown screen and hung. 

Is there any help please to fix that ?:(
I guess the problem from the NVIDIA driver if I am not wrong, I try to reinstall NVIDIA driver I did that a lot before and it went OK but this time every time I try to install the NVIDIA driver it says Unable to build the NVIDIA kernel module.

I will be grateful for any help. Thanks.:)

Best regards.
CFIL

---

### Post by sjnovick on 2008-11-02
The problem may be with compiz.  Log into a shell and type

# sudo apt-get remove compiz
# sudo apt-get remove compiz-core

Then try logging into Gnome and it should work.

Although compiz worked for my computer with 8.04, it doesn't work with 8.10.  I have an P3 Intel video card laptop.

---

### Post by CFIL on 2008-11-02
Thnak you sjnovick for the reply, I removed compiz but the problem still just brown background with my mouse pointer without anything. :(

Thanks for advance.

Regards:)

---

### Post by bhoemen on 2008-11-02
I have the same problem, i did a upgrade and also downloaded the cd and tryed it but all freeze at login.
when i type "sudo lshw -C video" to know what my video card is it says
" *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

any help will be greatly appreciated

---

### Post by TheGreenFox on 2008-11-03
Thanks I had the same problem and removing compiz worked\\:D/. I thought I would haft to reinstall from CD which would of been a real pain.:mad:

Thanks again.:popcorn:

---

### Post by CFIL on 2008-11-03
Good its work with you TheGreenFox, But I still have the problem and I am using WinXP which is a very bad I just trying to secure the system from spyware and virus which was not a problem with Ubuntu. 

I will be gratefull for any help. 

Regards.

---

### Post by Watchtow3r on 2008-11-03
Yeah I have a similar problem. I get to the login screen, but then when I type my username and password, it begins to login but then goes back to the login screen. I would try typing in the commands on the shell, but what is the command to log back out? Because once I type the commands to disable compiz I will have no idea how to get back out. Also, when I disable Compiz, will I be able to re-enable it later on and still be able to login? Because it's not really a fix if it just disables the source of the problem...



Edit: Ok disabling Compiz with Shell worked for me. I typed:


# sudo apt-get remove compiz
# sudo apt-get remove compiz-core

 But now how can I re-enable Compiz? Do I need to reinstall it? And do I need to do anything this time so that it works properly so I don't have the same problem? Thanks.

---

### Post by bhoemen on 2008-11-03
thanks heaps removing compiz worked for me..
just wondering why, s it because i don't have good graphics card or a bug or somethng else?

---

### Post by Watchtow3r on 2008-11-03
> **bhoemen said:**
> thanks heaps removing compiz worked for me..
just wondering why, s it because i don't have good graphics card or a bug or somethng else?

Yeah same here. Anyways What does it say for you under System>Administration>Hardware Drivers? For me it's blank, meaning I guess there are no drivers installed (which could be the cause of the problem. Also tell me if you find a way to re-enable compiz.

---

### Post by Watchtow3r on 2008-11-03
> **bhoemen said:**
> thanks heaps removing compiz worked for me..
just wondering why, s it because i don't have good graphics card or a bug or somethng else?

Hey also I haven't gotten Compiz to work yet, but I think I'm getting there. Make sure that you have the Universe and Multiverse repositories turned on in Synaptic. Mine weren't for some reason after this update and I think that's partly the problem since I couldn't get the drivers for my computer.

Update: Finally!! Got it working. After enabling all those repositories and also the proposed and backports updates, as well as all the other updates listed in Software Sources, I just tried re-installing Compiz from Synaptic and it worked.

---

### Post by bhoemen on 2008-11-03
> **Watchtow3r said:**
> Yeah same here. Anyways What does it say for you under System>Administration>Hardware Drivers? For me it's blank, meaning I guess there are no drivers installed (which could be the cause of the problem. Also tell me if you find a way to re-enable compiz.
my hardwae drivers is blank too

---

### Post by jerrylamos on 2008-11-03
> **Watchtow3r said:**
> 
Edit: Ok disabling Compiz with Shell worked for me. I typed:

# sudo apt-get remove compiz
# sudo apt-get remove compiz-core

 But now how can I re-enable Compiz? Do I need to reinstall it? And do I need to do anything this time so that it works properly so I don't have the same problem? Thanks.

From fighting this problem for two months, see Launchpad Bug #259385:

The 8.10 compiz developers are exploiting fancy new graphics features on what high end cards I don't know.  These exploitations for "eye candy" stop many Intel graphics cards freezing the computers.  That is a LOT of computers.  Ubuntu 8.04 compiz will work, if you want to take 8.10 off and go to 8.04.  8.04 has long term support so can be used for quite a while.

The "Official Fix" is to "blacklist" video hardware that the new compiz code doesn't work on, and then compiz is not run on that hardware.  Period.  

If you want to try compiz again, then you can install compiz with Synaptic.  If it broke before it will break again.

Good luck, Jerry

p.s. My IBM Thinkpad R31 1 gHz with Intel Graphics runs very nicely on 8.10 without compiz.  BBC videos & you tube videos quite usable.

---

### Post by Watchtow3r on 2008-11-03
> **bhoemen said:**
> my hardwae drivers is blank too

Yeah but all it means is that there are no proprietary drivers installed. There could still be some open-source ones installed. Don't worry about it. Do everything I did and see if it works.

---

### Post by CFIL on 2008-11-03
It seems will not work with me by trying to remove just compiz. Now I am thinking to downgrade the system to 8.04 .. Is there anyway to do that and save my files ? because I do not want to install clean copy so it will be delete all my settings and files. :(

---

### Post by Watchtow3r on 2008-11-04
I'd say give it another day or two of tinkering before you decide to downgrade. But I do know that downgrading tends to be very complicated and hard, so your best bet is to save your files to an external hard drive then wipe the whole system, then do a clean install. I think there's also a way to save settings but I'm not sure how.

---

### Post by SHato on 2008-11-16
Hi all,
I've got similar problem with booting to the system. I could not login after upgrade from 8.04 to 8.10 because login screen will not display.. I see only black screen and system doesn't answer (only ctrl+alt+del will restart). Then I tryed to fix X-server and it works because it disabled my ATI graphic card.. So when is my graphic card enabled i can't login :(

i tryed to remove compiz too, but with no effect.. 

thanks much for your replies.. 

SHato::

---

