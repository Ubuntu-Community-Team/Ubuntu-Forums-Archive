---
title: "[SOLVED] Network|Windows Network members no longer visible after 7.10RC upgrade"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by henkjan on 2007-10-15
I've been running 7.04 with a wireless connection to my router. I've also got a NAS device and two XP hosts on the home network (one of which shares a printer). Before the upgrade to 7.10, I could print from Ubuntu to the shared printer, and use Samba to share home directories from Ubuntu back to the XP hosts. All three hosts and the NAS were visible in Places|Network|Windows Network.

This morning I upgraded to 7.10 and after the reboot, the Ubuntu host can no longer see the members of the Windows Network or print to the shared printer. The wireless connection from Ubuntu to the router still works fine for Internet access, and the Windows hosts can still see each other, but cannot access the Ubuntu Samba shared home directories.

Also, the Firestarter window won't show - when I try to run it from System|Administration|Firestarter I see 'Starting Firestarter' in the panel for a few seconds, but the window never shows.

Anyone else experience networking problems after installing the 7.10RC? I think the upgrade replaced netkit-inetd with the openbsd-inetd package (and Synaptic won't allow re-installation of netkit-inetd "Package netkit-inetd has no available version, but exists in the database."). My assumption is that something needed for the Windows Network to work has been changed by the upgrade but I'm not sure what...

---

### Post by henkjan on 2007-10-16
Update:

I've run
[FONT="Courier New"]
sudo apt-get update[/FONT]

Followed by

[FONT="Courier New"]sudo apt-get upgrade[/FONT]

Which downloaded a few meg of stuff.

Then I modified the [FONT="Courier New"]/etc/sudoers[/FONT] file line for Defaults to add the bolded text

[FONT="Courier New"]Defaults        !lecture,tty_tickets,!fqdn,**env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"**
[/FONT]
And now can bring up the [FONT="Courier New"]Firestarter[/FONT] window again.

If I stop the firewall, and open [FONT="Courier New"]Places|Network[/FONT]  at first I can only  see my NAS device. If I wait a while and refresh, I can also see my Ubuntu laptop, but still can't see the two XP hosts. Wait a bit longer still and refresh, and I can see the XP host that shares the printer. A bit more patience and finally the other XP host shows up.

Can anyone tell me why this would be? Under 7.04 I ran the firewall and was able to see the local Windows Network hosts. After the 7.10 upgrade, it looks like I can only see the local Windows Network hosts if I stop the firewall and wait a while. Even if I do sit behind a Router's firewall, I'd prefer a solution that doesn't require turning off my Ubuntu firewall...

---

### Post by henkjan on 2007-10-17
Update:

Now that the Firestarter GUI runs for me, I made progress on this.

1. Open Firestarter.
2. [FONT="Courier New"]Edit|Preferences[/FONT]. Ensure '[FONT="Courier New"]Apply policy changes immediately[/FONT]' is checked. [FONT="Courier New"]Accept[/FONT]
3. Select [FONT="Courier New"]Events[/FONT] tab.
4. From [FONT="Courier New"]Panel,[/FONT] open [FONT="Courier New"]Places|Network[/FONT] to generate some network traffic

See what entries you get for[FONT="Courier New"] Blocked Connections[/FONT] [e.g.[FONT="Courier New"] Samba (SMB)[/FONT]]. Right-click one of them and select '[FONT="Courier New"]Allow Inbound Service for Everyone[/FONT]', which will create a [FONT="Courier New"]Policy[/FONT] opening the [FONT="Courier New"]Samba (SMB)[/FONT] port. You can edit the [FONT="Courier New"]Policy[/FONT] entries with a right click I ended up opening[FONT="Courier New"] Sun-RPC portmap[/FONT] too. Now I can see my XP hosts and NAS device again.

---

### Post by henkjan on 2007-10-18
I found [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access") thread, where there is an excellent explanation of Firestarter, iptables and Samba. This kind of stuff is very helpful to an Ubuntu noob like me.

Wish I'd found it earlier :)

---

