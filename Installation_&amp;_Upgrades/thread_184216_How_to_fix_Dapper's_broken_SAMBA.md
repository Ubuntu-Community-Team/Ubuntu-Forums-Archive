---
title: "How to fix Dapper's broken SAMBA ??"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by celem on 2006-05-29
:confused: 
I used to be able to access Windows XP shares and the Windows XP box could access the Dapper shares, but after Dapper daily updates last week Samba has become totally broke. 

When I try to access the Dapper shares via “Start->My Network Places”, the Dapper shares do not display.

When I try to access the Dapper shares via “Start->My Network Places->View Workgroup Computers”, the Dapper machine icon displays, but when I click on it, it fails with a “The network path was not found” error dialog box.

When I try to access the Windows shares from Dapper via Places-Network Servers, the Windows Network icon is displayed but when I click on the icon, the dialog box window clears to a blank and the shares do not display.

/etc/smb.conf is generic original except that I have added a share at the bottom (via the GUI). The workgroup is the same name as the XP box, “MSHOME”; security-user; netbios = alvin.

**Remember **– _all of this worked correctly prior to last week’s Dapper daily updates_.

Because some people have indicated that they are successfully using Samba with Dapper I have attempted another try at fixing it.

1.    Using Synaptic I totally removed, including configuration files, ALL packages dealing with Samba. The packages removed were: samba, samba-common, libsmbclient, smbclient, smbfs, libgnomevfs2-extra

2.    I rebooted Dapper and verified that /etc/rc?.d/*sambs, /etc/initd/samba, /etc/samba/* were all gone.

3.    Using Synaptic I added only samba and samba-common and repeated attempts to access Windows shares and visa-versa. The results of accessing Dapper shares from Windows had the same “The network path was not found” error. Accessing Windows shares from Dapper resulted in a "smb:/// is not a valid location." Error. This error is why I originally  added libgnomevfs2-extra.

4.    I tested printing to the Windows XP shared printer and it, once again, wasn’t working. So, I next used Synaptic to add back libsmbclient, smbclient, smbfs and libgnomevfs2-extra. Then I rebooted Dapper.

5.    Now the Windows XP shared printer works but access shares to/from is back to the original problem – Windows reports “The network path was not found” and Dapper shows a blank dialog box when I click the “Windows Network” icon at Places-Network Servers.

[B]Can anyone think of anything else to try? This is driving me nuts.
[/B]

---

### Post by celem on 2006-05-29
Update: Still broken as described yet if I use Firefox to access "smb://192.168.0.102/", I see the Windows shares in the browser. Any clue as to what is broken in the normal packages??

---

### Post by goodmaj on 2006-05-29
Make sure that /etc/samba/smb.conf reads as follows:

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

I got the same error message with Samba shares on Mac OS X 10.4 until I made the above change in the conf file. (encrypt passwords = true)

After changing the conf file you must restart samba to make the change effective.

I hope this helps.

---

### Post by celem on 2006-05-29
"encrypt passwords = true" is set because that is the default in smb.conf. I suspect that whatever in the daily Dapper updates broke Samba wasn't in a Samba package, as I have replaced those several times, but instead, must be another package that interacts with Samba.

---

### Post by celem on 2006-05-29
To re-phrase and clarify the problem, I feel that it isn&#8217;t a Samba problem, but rather a nautilus problem, or combination thereof, in that the Samba info isn&#8217;t being displayed. Since the Windows shares can be viewed via Firefox with "smb://192.168.0.102/", yet only a blank screen results from looking for the shares via nautilus&#8217;s &#8220;Places->Network Servers&#8221;.

---

### Post by Fedcer on 2006-05-29
[QUOTE=celem]To re-phrase and clarify the problem, I feel that it isn&#8217;t a Samba problem, but rather a nautilus problem, or combination thereof, in that the Samba info isn&#8217;t being displayed. [/QUOTE]

I don't think that it's a nautilus problem because I'm using Kubuntu Dapper and I'm having exactly your same problem. After one of dapper's updates samba stopped working and when I try to access a computer in the newtork I get the error "The network path was not found" (while before with the same config it had been working perfectly).

---

### Post by celem on 2006-05-29
I am concerned that this will not be fixed since other Dapper users report no problems with Samba. I don't know what would be unique to mine and your loads yet not in other people's Dapper loads. I upgraded to Dapper Beta weeks ago from Breezy 5.10. Originally I had problems printing to my Windows Printer but this Samba problem was fixed. Subsequent to that fix all aspects of Samba worked bidirectionaly to/from Windows. Then, last week's upgrades broke something - I don't know what. I am concerned that my last resort will be to do a clean install with Dapper's final release but I hesitate in doing that because I don't want to lose everything that I've configured, such as qemu and wine.

---

### Post by jalonsom on 2006-05-29
I experience a similar problem since a long time ago.
I think it is a problem with resolving server names:

In nautilus, press ctrl-l to show the address when you have tried to browse the server and it has failed. It shows "smb;//servername". Nautilus is trying to find the server by its name.

Replace the server name with its IP and  it should work ok.

That's why I guess it is a name resolving problem. What I don't know is if it's a bug or a misconfiguration of samba... Probably a bug as it does not work for me out of the box, with the default config...
It happens to me when browsing both WinXP and Dapper machines.

Gonna take a look at launchpad to see if there is something similar.

---

### Post by pauljwells on 2006-05-29
If you have your networkset up using dhcp it might just be that your router has the wrong names against IP addresses in its leases table. I find that most SAMBA funnies get magically fixed with a router reboot.

---

### Post by celem on 2006-05-29
Except, (see my problem description above) it worked prior to last week's Dapper Daily Updates. Nothing else changed in my Windows XP box, router, network, etc. Even the Dapper box had no changes other than the Daily Updates. Therefore, logically speaking, the problem must be within changes made in Dapper by the updates.

---

### Post by celem on 2006-05-29
Ok, I tried what "jalonsom" suggested. I went to "Places-Network Servers", then clicked on the Windows Network icon, which, as before, showed a blank display. Then I entered a control-L on the blank display and the address line showed "smb:///". I then inserted the IP address of the window box into the proper spot in the address line, i.e., smb://192.168.0.102/, and it correctly displayed the Windows XP share icons. This is a manual fix as the screen remains blank when I repeat the process. I am closer to the problem. Any idea as to why nautilus isn't resolving server names?

---

### Post by dglock on 2006-05-29
I presume you are using ubuntu, I am using kbuntu and have no problem using samba shares.

  I have two windows comps and three linux comps on my lan and all are available through samba, using the default installation. I will check my ubuntu partition and see if it works there.

don

---

### Post by Fedcer on 2006-05-29
I've also tried with jalonsom's suggestion and it worked here too.

The problem maybe is (and I'm guessing here) that a file that contains the server names and it's network IPs is messed up. The thing is I have no idea if this file exist or were to find it.
It doesn't look like a specific problem of nautilus because the same is happening to me with konqueror.

---

### Post by panabar on 2006-05-29
[QUOTE=pauljwells]If you have your networkset up using dhcp it might just be that your router has the wrong names against IP addresses in its leases table. I find that most SAMBA funnies get magically fixed with a router reboot.[/QUOTE]

Thank You!
Now I can access samba shares on a Mac Os, and Windows Xp from ubuntu, but I can not access ubuntu from outside. :) :(  (Edited line)  and print to a shared printer  :) Thank You again!

Windows keeps asking for a password and when I enter one it asks again (no matter if I enter my ubuntu password or another with or without my username). Mac kept asking for a password but somehow in the 8th or so attempt a connected without a password.  In my second try (after unmounting my publicfolder from mac) mac did not connect.
Samba is weird.

---

### Post by celem on 2006-05-29
Re your password prompt from Windows, when Samba was working for me (yes I use Ubuntu) smbpasswd fixed the prompt issue. execute smbpasswd --help or man smbpasswd for usage.

---

### Post by jalonsom on 2006-05-29
panabar: Do what celem says (it's the secure way) or change 
security=user 
to
security=share
in /etc/samba/smb.conf
This will allow browsing folders without authentication, but is less secure. There are lots of information in this forum about this.

Anyway this is not the main problem that originated this thread.

---

### Post by djsroknrol on 2006-05-29
I found that after a couple of updates, the process unchecked Samba in System>Asministration>services believe it or not...check that Samba is checked in there...just a thought...

---

### Post by jalonsom on 2006-05-29
Thanx djsroknrol but i guess samba is running as we can browse samba shares, as long as we use ip addresses instead of names.

I have searched in the forums a bit and found 3 threads dealing with similar problems, but they were no use to me, maybe they work for you:

[http://www.ubuntuforums.org/showthread.php?t=182824]("http://www.ubuntuforums.org/showthread.php?t=182824")
[http://www.ubuntuforums.org/showthread.php?t=180844]("http://www.ubuntuforums.org/showthread.php?t=180844")
[http://www.ubuntuforums.org/showthread.php?t=88206]("http://www.ubuntuforums.org/showthread.php?t=88206")

PLEASE:
Could you check in a terminal to do 'ping servername'
I'm especially interested to see if people that have working sambas can ping by servername, because I can't and this can be at the cause of the problem.

---

### Post by celem on 2006-05-29
Samba &#8220;is&#8221; checked in System>Asministration>services.

Yes, I can &#8220;ping&#8221; the windows box &#8220;192.168.0.102&#8221;, but I expected that I could because when I insert the IP address of the window box into the proper spot in the address line, i.e., smb://192.168.0.102/, and it correctly displayed the Windows XP share icons, indicating that the network connection works but the name lookup fails.

I wonder if the problem isn&#8217;t in &#8220;nmbd&#8221;, which is part of the Samba suite. I quote&#8221; nmbd is a server that understands and can reply to NetBIOS over IP name service requests, like those produced by SMBD/CIFS clients such as Windows 95/98, Windows NT and LanManager clients. It also participates in the browsing protocols which make up the Windows "Network Neighborhood" view.&#8221;.

By the way, with ps &#8211;A, I notice that two instances of &#8220;smb&#8221; are running and 1 instance of nmbd. Is two instances of &#8220;smb&#8221; normal. Enter pgrep smb and see how many processes you are running?

---

### Post by jalonsom on 2006-05-29
This is really a weird problem. I hadn't realized earlier because I have permanently mounted all the shares I need so they work OK:

I have seen that sometimes I can do Network>Windows network>workgroup so I can see the servers present, but trying to open one leads to the error described.

But other times I can do Network>Windows network>workgroup and I only see the local computer (browsing local computer always works)

And at other times I can just do Network>Windows network and a blank screen appears. This is what celem described.

Crazy...

---

### Post by panabar on 2006-05-29
Celem and Jalonsom
Thank You! :) Now I can access ubuntu from windows and mac :)

Jalonsom I tried pinging with the servername, the output is

```
panabar@breakdownlp: ~ $ ping \OSK
ping: unknown host OSK
```

and at first I couldn't change my smb password because I didn't know my old password (actually I didn't even know it existed), so smbpasswd gave errors.

So I removed and added my user using root mode of smbpasswd and setup a new password, now everything is as it should be :)
Thank You 
:)

---

### Post by jalonsom on 2006-05-29
celem: I was asking if people could ping the servers not by specifying the IP but the name of the server. I already thought that you would not be able to ping by the name, as you have the same problem as me, but just wanted to check if people with configurations that work ok could do it.

I had 5 (!!) smb processes running. I restarted samba and now I have 2 smb processes running. I wonder if this is normal.

Yes, it looks that nmbd could be the cause. I'll do a little search on that.

Thanks panabar. Glad to hear it works now!

---

### Post by jalonsom on 2006-05-29
celem: I was asking if people could ping the servers not by specifying the IP but the name of the server. I already thought that you would not be able to ping by the name, as you have the same problem as me, but just wanted to check if people with configurations that work ok could do it.

I had 5 (!!) smb processes running. I restarted samba and now I have 2 smb processes running. I wonder if this is normal.

Yes, it looks that nmbd could be the cause. I'll do a little search on that.

Thanks panabar. Glad to hear it works now!

---

### Post by celem on 2006-05-29
Since I am not alone, I believe that there is some sort of bug there, so I submitted bug# 47386 at launchpad.

---

### Post by pauljwells on 2006-05-29
For what it's worth, if you use a dhcp network, edit your /etc/dhcp3/dhclient.conf to include the line:

```
send host-name "your-machine-name-here"
```

remember to delete the leading '#'

this will make sure that after every reboot of either pc or router you should get valid hostnames in the dhcp lease list. I found this out through wanting to use

```
ssh -X hostname
``` on my dhcp network, but it might help with Samba too.

---

### Post by Fedcer on 2006-05-29
Hi, I tried pinging the servername and at first it seemed to be working (which surprised me). So I took a closer look and realized that the IP it was pinging was 127.0.0.1 (it happens with all the servernames). It's quite strange.

---

### Post by celem on 2006-05-29
pauljwells, I looked at /etc/dhcp3/dhclient.conf and it contains some strange stuff. I am using eth1 (WiFi) and it only references eth0. Also, all of the references are to alien site - not me. My machine's name is "alvin" and I have no domain. I don't know who "andare.fugue.com" is?

here is my /etc/dhcp3/dhclient.conf:
--------
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by pauljwells on 2006-05-29
@celem

you don't need to worry about the rest of the file. All the lines that begin with # are ignored, so you can see most of it is just boilerplate. The only thing you need to do is edit the line

```
#send host-name "andare.fugue.com";
```

to read

```
send host-name "whatever you want to call your machine";
```

then it's safest to shut everything down, restart the router then restart all your machines. Then you can check the leases list on your router and you should see the names for any machines you set.

---

### Post by dtfinch on 2006-05-29
I guess I haven't said anything because I gave up on it probably a year ago, but I've always had trouble accessing network shares in nautilus. The problems vary, and I have zero difficulty accessing samba shares on these systems from my XP system. Currently, I'm not asked for a login, I don't see all the shares, and when I try to connect to the shares I do see, it says they don't exist. I'd give more information, but this being a home network the problem hasn't been serious enough to really investigate. I could always mount shares from the command line, but I hoped it would be done automatically someday.

I've used Ubuntu once on a network with a windows domain, where WINS was all set up properly, and everything seemed to work fine. That was a long time ago though, back in the warty/hoary days.

---

### Post by celem on 2006-05-29
No joy, "pauljwells". I edited into /etc/dhcp3/dhclient.conf my Ubuntu machine name and rebooted everything, yet the bug remains wherein the Windows XP shared printer works but share access between Ubuntu and XP retains the original problem &#8211; Windows reports &#8220;The network path was not found&#8221; and Dapper shows a blank dialog box when I click the &#8220;Windows Network&#8221; icon at Places-Network Servers.

---

### Post by trakeen on 2006-05-30
samba used to work fine for me before the last update, now it seems to have stability issues. If I try and copy an 8gb file from my windows machine to unbuntu (using unbuntu) it only copies 4gb and it's really slow while copying. Copying from windows to unbuntu doesn't work either, actually causes explorer to crash after a certain amount of time (and the network utilization drops to %0 for long amounts of time)

I don't have any problems seeing shares or anything but I can't do anything with them since the copies always fail (and I need to copy about 400gb over the network)

---

### Post by thumper on 2006-05-30
I get the same problem mounting a network share with smbfs.

After a while transferring files (for some small definition of a while) the copy freezes and network utilization drops to 0%.

No errors shown in the log files.

---

### Post by celem on 2006-05-30
Well, now I can add myself to the "intermittent" category. I consider Samba to have problems, but, for now, my windows shares are working. How they came to work again is not reassuring. I have been using the same Avaya Wireless Gold 802.11 card for months. I have not changed the card during the period that Samba shares worked or after they broke. However, today, while working on a friend&#8217;s old Windows 98se laptop, I needed the Avaya Wireless Gold 802.11 card to put into his laptop because his old machine wouldn&#8217;t physically accept any of the other WiFi cards that I had (32 bit Cardbus vs 16 bit PCMICA issue). Anyway, has the 16-bit PCMCIA configuration (small tab) so I pulled it from my Dapper machine and put it into the windows laptop and then plugged a Linksys 32-bit cardbus WiFi card into the Ubuntu box. Miricles of miracles, Dapper Samba shares started working again!

I am not comforted by this bit of magic &#8211; I still think that something is wrong with Samba.

Another interesting anomaly that happened simultaneously with the origin of the Samba problems is that my Icon for System->Administration->Printers disappeared. My only printer is a Deskjet 895Cse on my Windows XP box, via Samba share. It still works but the System->Administration->Printers Icon is gone so I cannot add more printers or change the printer defaults. I feel that this related to the Samba share issue because the Printer Icon disappeared simultaneously with the problem of Samba not being to see the shares.

---

### Post by jalonsom on 2006-05-30
[QUOTE=celem]Well, now I can add myself to the "intermittent" category.[/QUOTE]

Welcome!

I might have an idea of what could be the reason for this intermitence.
I think it depends on which computers are on an in what order they are on, because in the samba logs (log.nmbd), sometimes my main dapper machine (I have also a dapper server and a WinXP laptop) is the local domain controller and sometimes it seems that it is not. Even sometimes there are logs saying that it has become the domain controller and 5 or 6 seconds later it stops being it...
But I have to check it more carefully.

I'll try to increase the verbosity of logs and see what is happening.

---

### Post by nix4me on 2006-05-30
My samba works fine.  i had to type the ip of the dapper machine in the address line on windows explorer, i could then map the folders to drives on the windows machine.

Works just fine.

nix4me

---

### Post by celem on 2006-05-30
Ahh, but that IS the problem. You should not have to type in the IP of the share. You don't have to on Breezy and you didn't have to on Dapper until recently. Read all of the above and you'll see that Samba, and probably nmbd, has a problem.

---

### Post by nix4me on 2006-05-30
Doesnt bother me, ive never noticed.  I assign static ips on my network.

nix4me

---

### Post by jalonsom on 2006-05-30
[QUOTE=nix4me]Doesnt bother me, ive never noticed.  I assign static ips on my network.

nix4me[/QUOTE]

That's what happened to me. I could live with it because I knew what a static ip was, so I didn't bother.
But the fact is that some of us cannot correctly browse the network, and many people, especially newbies, need this feature.

This bug may be quite common, as many people have surely done the same.

---

### Post by Video Toaster on 2006-05-30
I just updated my Ubuntu install and found that I could navigate to my Windows computer by typing in the address (smb://WINDOWSCOMPUTER/) 
in Nautilus.  I can also navigate to my Ubuntu computer from the Windows PC.  However, if I double-click my computer in Nautilus, I'm told:
> The filename "WINDOWSCOMPUTER" indicates that this file is of type "desktop configuration file".  The contents of this file indicate that the file is of type "x-directory/smb-share".  If you open this file, the file might present a security risk to your system.
What?

BTW, the two computers are in different workgroups... not sure if that matters.

EDIT:  Clarify what I meant by "address"

---

### Post by celem on 2006-05-30
I think that you are missing the point. It doesn't matter if you use static IP or DHCP. When you click Places->Network Servers, a "Windows Network" Icon should appear. If you then click the "Windows Network" Icon you should see an icon of the workgroup, MSHOME in my case. If you then click  the icon of the workgroup you should see icons of the share folders appear. If you then click the those share folder icons you will see the files on the networked machine. The point is that it should all be graphical and not require entering any IP at all.

---

### Post by Video Toaster on 2006-05-30
[QUOTE=celem]I think that you are missing the point. It doesn't matter if you use static IP or DHCP. When you click Places->Network Servers, a "Windows Network" Icon should appear. If you then click the "Windows Network" Icon you should see an icon of the workgroup, MSHOME in my case. If you then click  the icon of the workgroup you should see icons of the share folders appear. If you then click the those share folder icons you will see the files on the networked machine. The point is that it should all be graphical and not require entering any IP at all.[/QUOTE]
If that was to me, I don't think I was clear enough... by address I meant the computer name with smb:// in front.  I was able to browse the network fine, but just couldn't open the computer because it was complaining about MIME types.

---

### Post by celem on 2006-05-31
My comment was to "Video Toaster" but it applies to you as well if you cannot access your shares "graphically" and must use smb://machine_name to access the shares.

---

### Post by cbudden on 2006-06-01
I think the problem is resting with nautilus.  At the same time the shares come up fine in Konqueror but fail to appear in Nautilus.

---

### Post by jalonsom on 2006-06-01
I can browse my network!!!

I did a fresh install of Dapper just to see if it would make any difference, but it didn't. No browsing.

Then I found a [bug]("https://launchpad.net/distros/ubuntu/+source/samba/+bug/39717") on permissions for guests and I decided to try to see what was the effect.
The idea is to activate the guest account by typing

# enable nobody user
sudo smbpasswd -e nobody
# set nobody to no password
sudo smbpasswd -n nobody

Bingo! after a small time (not inmediately) I was able to perform a "smbtree" and to browse the network with nautilus.
Maybe there was a permissions problem somewhere...

This is a really annoying bug, and it should be addressed asap.

---

### Post by llamakc on 2006-06-01
I too am stuck in this rut:

I've put my Kyocera-Mita FS-1200 connected directly to my Ubuntu Dapper box and local printing is perfect.

I want to share a 'share' on Ubuntu with my wife's XP box, and for her to be able to print to the FS-1200.

I've made many of the changes listed all over the forums and am stuck with this when I try to smbtree:
[code]
root@vulva:/etc/samba# smbtree
params.c:Parameter() - Ignoring badly formed line in configuration file: +########## Domains ###########
Password:
WORKGROUP
        \\VULVA                         vulva server (Samba, Ubuntu)
failed tcon_X with NT_STATUS_ACCESS_DENIED
        \\PYLON                         Melissa's Computer
                \\PYLON\C$              Default share
                \\PYLON\ADMIN$          Remote Admin
                \\PYLON\KyoceraF        Kyocera FS-1200 (KPDL-2) (Copy 1)
                \\PYLON\print$          Printer Drivers
                \\PYLON\D$              Default share
                \\PYLON\IPC$            Remote IPC
[\code]

Ignore the Kyocera for Pylon: I _just_ moved that printer off of there and haven't deleted the printer entry in XP yet.

Of course there have been plenty of /etc/init.d/samba restarts....

---

### Post by cbudden on 2006-06-01
If I type smbtree after enabling the nobody user I see the shares in the printout, but they still don't come up in nautilus.  Also, I left the nobody user password blank.

---

### Post by llamakc on 2006-06-01
I opened ports 445 and 631 on the XP box and now it can correctly browse the network and see my printer. However it gets the 'access denied - unable to connect' error.

So close and so far away...

---

### Post by llamakc on 2006-06-01
I know can smbtree properly:

```

root@vulva:/var/log/cups# smbtree
params.c:Parameter() - Ignoring badly formed line in configuration file: +########## Domains ###########
Password:
WORKGROUP
        \\VULVA                         vulva server (Samba, Ubuntu)
                \\VULVA\HP7200          HP7200
                \\VULVA\FS-1200         FS-1200
                \\VULVA\ADMIN$          IPC Service (vulva server (Samba, Ubuntu))
                \\VULVA\IPC$            IPC Service (vulva server (Samba, Ubuntu))
                \\VULVA\Absol-Shared
                \\VULVA\print$          Printer Drivers
        \\PYLON                         Melissa's Computer
                \\PYLON\C$              Default share
                \\PYLON\ADMIN$          Remote Admin
                \\PYLON\print$          Printer Drivers
                \\PYLON\D$              Default share
                \\PYLON\IPC$            Remote IPC

```

Weirdness. So Dapper released today? I would have figured this would just work automagically.

---

### Post by llamakc on 2006-06-01
I am such a tool. I had a malformed IP/netmask in cupsd.conf!

All fixed.

---

### Post by ixfnak on 2007-11-16
Regarding name resolutions issues, it looks like nmbd is broken. Please see:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042)

In the meantime, you can use the IP address instead of the netbios name to access shares as noted above:

\\ipaddress\sharename

It looks like some people are having authentication problems as well, but that would be independent of name resolution.

If you are use dhcp, you can always run ifconfig on the samba server host computer to get the current IP address to use when addressing shares. Keep in mind that the IP address in that case may change between boots.

---

### Post by ixfnak on 2007-11-18
The security updates I applied this morning (2007-11-18) Central European Time fixed the problem. nmbd is now working and with it NetBIOS name resolution from a Windows XP client.

---

### Post by Anubis on 2007-12-26
And now its broken in Gutsy...sad.:confused:

---

### Post by calif99x on 2008-05-24
Hi:

I came across this thread as I recently ran into the problem with Gutsy, upgraded to Hardy (8.04 LTS) and still have the same problems.  After much dinking around, I can now see the shares from Windows, and can access 3 of 6 shares. 

The 3 that can be accessed are owned by root:root versus the other 3 non-working shares that are fred:fred.  Changing the ownership does nothing.

Getting kind of fed up with this problem.

---

### Post by celem on 2008-05-31
I too am getting rather fed up with this issue. Whenever I have gotten it working somewhat, an update breaks it again. With Gutsy it worked but VERY SLOWLY. Now that I've upgraded to Hardy its totally broken again and I can't seem to get it to work. Something that is so brainlessly simple with windows shouldn't remain a constant problem with Linux.

---

