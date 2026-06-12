---
title: "Network Manager unable to connect to PPTP VPN"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by flanker on 2008-09-17
Has anyone been able to connect to a Microsoft VPN server using PPTP with the latest version of Network Manager in Intrepid?

Each time I try, the connection fails, displaying a pop-up message that says: The VPN connection failed because the VPN service stopped unexpectedly.

I can connect to the VPN server successfully using Hardy.

A bug report has been filed but is yet to be confirmed.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168)

Configuration;
Client Configuration: MSCHAPv2/MPPE/Stateful enabled, all other options disabled.
network-manager-pptp version: 0.7~~svn20080908t183521-0ubuntu1
VPN Server: Win2k3 RAS/PPTP

Syslog Output;
```

Sep 14 17:37:34 laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Sep 14 17:37:34 laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 9045 
Sep 14 17:37:34 laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Sep 14 17:37:34 laptop NetworkManager: <info>  VPN plugin state changed: 1 
Sep 14 17:37:42 laptop NetworkManager: <info>  VPN plugin state changed: 3 
Sep 14 17:37:43 laptop NetworkManager: <info>  VPN connection 'work' (Connect) reply received. 
Sep 14 17:37:43 laptop pppd[9057]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Sep 14 17:37:43 laptop kernel: [  428.080729] PPP generic driver version 2.4.2
Sep 14 17:37:43 laptop pppd[9057]: pppd 2.4.4 started by root, uid 0
Sep 14 17:37:43 laptop pptp[9064]: nm-pptp-service-9045 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Sep 14 17:37:43 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Sep 14 17:37:43 laptop pppd[9057]: Using interface ppp0
Sep 14 17:37:43 laptop pppd[9057]: Connect: ppp0 <--> /dev/pts/0
Sep 14 17:37:43 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Sep 14 17:37:43 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 59813). 
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Sep 14 17:37:44 laptop pppd[9057]: LCP terminated by peer (^HM-OX^D^@<M-Mt^@^@^BM-3)
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Sep 14 17:37:44 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Sep 14 17:37:47 laptop pppd[9057]: Connection terminated.
Sep 14 17:37:47 laptop pptp[9064]: nm-pptp-service-9045 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Sep 14 17:37:47 laptop pptp[9064]: nm-pptp-service-9045 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Sep 14 17:37:47 laptop pptp[9075]: nm-pptp-service-9045 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Sep 14 17:37:47 laptop pptp[9075]: nm-pptp-service-9045 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Sep 14 17:37:47 laptop pptp[9075]: nm-pptp-service-9045 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Sep 14 17:37:47 laptop pppd[9057]: Modem hangup
Sep 14 17:37:47 laptop pppd[9057]: Exit.
Sep 14 17:37:47 laptop NetworkManager: <info>  VPN plugin state changed: 6 
Sep 14 17:37:47 laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Sep 14 17:37:59 laptop NetworkManager: <debug> [1221410279.586815] ensure_killed(): waiting for vpn service pid 9045 to exit 
Sep 14 17:37:59 laptop NetworkManager: <debug> [1221410279.587075] ensure_killed(): vpn service pid 9045 cleaned up 

```

---

### Post by Sophont on 2008-09-18
I also need PPTP VPN to connect to office (W2K, W2K3, Vista).

Problems with VPN is the main reason I haven't upgraded to Intrepid yet.

I was hoping that Alpha 6 will fix this.
I'll check that as soon as it is available.

Works well enough on Hardy - only problem is that MTU can't be changed from NM (though an edit field suggests it does :-) ) - but that's easily worked around by a script after VPN connection is established.

Does the MTU field work with NM 0.7?

flanker - you mentioned in Bug #259168 that you can connect via terminal - how do you do that?

---

### Post by flanker on 2008-09-23
Check out the section at the bottom of this URL, [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
I've included my settings below.

cheers, Ian.

```
ian@laptop:~$ egrep -v "^#|^$" /etc/ppp/peers/quest
remotename PPTP
ipparam xxxx
pty "pptp xxxx --nolaunchpppd"
name xxxx
usepeerdns
require-mppe-128
refuse-eap
noauth
file /etc/ppp/options.pptp

ian@laptop:~$ egrep -v "^#|^$" /etc/ppp/options.pptp
lock
noauth
refuse-pap
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
```

---

### Post by Steve1961 on 2008-09-23
This really is a bit of a deal breaker.  the pptp plugin works fine in hardy, but I would really like the 3g support in network-manager 0.7.  But until I can get both it's not worth the upgarde,

---

### Post by Nullack on 2008-09-23
> **Sophont said:**
> I also need PPTP VPN to connect to office (W2K, W2K3, Vista).

Problems with VPN is the main reason I haven't upgraded to Intrepid yet.

I was hoping that Alpha 6 will fix this.
I'll check that as soon as it is available.

Works well enough on Hardy - only problem is that MTU can't be changed from NM (though an edit field suggests it does :-) ) - but that's easily worked around by a script after VPN connection is established.

Does the MTU field work with NM 0.7?

flanker - you mentioned in Bug #259168 that you can connect via terminal - how do you do that?

No, I raised another bug about the MTU field not working

If you replicate the original posters bug you could confirm the bug by moving the status to confirmed. Note confirming a bug isnt saying confirmed in a bug comment.

Also if this bug is a regression, it can be tagged appropriately as per:

[http://ubuntuforums.org/showthread.php?t=924782](http://ubuntuforums.org/showthread.php?t=924782)

---

### Post by Sophont on 2008-09-25
Meanwhile I tried Alpha 6 live, but can't reproduce above bug per se because I don't even get that far. Even after installing PPTP package the Add button under VPN Tab remains disabled.

Somebody pointed me to a PPA that I will try next time I boot Intrepid.

---

### Post by leech on 2008-09-25
I have a stranger issue.  I can add a new VPN connection, I choose pptp, under Advanced I can click "Use Point to Point Encryption (MPPE) and select 128bit, but then it doesn't save the settings once I hit Ok....

How utterly annoying.  Hardy works fine.  I was really hoping to get this going, but since I've already spent two nights trying to get various VPN stuff working, I'm about to just run amok!

Leech

---

### Post by tact on 2008-10-07
Ok got it sorted.  The new networkmanager in intrepid does not have an option to "refuse EAP" and that is essential to many PPTP type VPN connections.

I found a thread that hit on the answer...  go into gconf and add a new string key called "refuse-EAP" and set its value to "yes"

where to put this new key - when you are in the gconf editor navigate to /system/networking/connections/x/vpn

"x" will be a number representing the connection...  mine was 5, yours may be different.

You still need to set MPPE on and stateful...  should work then.

---

### Post by mbeierl on 2008-10-07
What a journey, but rolling back to hardy for:

network-manager
network-manager-gnome
network-manager-pptp
libnm-util0
libnm-glib0

did the trick for me.  The only note of caution is: be sure to download the hardy debs first before "removing" the intrepid versions as you may end up without a network for a while during the downgrade :)

As far as those comments about pptp being broken and that being a deal-breaker goes: remember, intrepid is still in alpha, not everything is guaranteed to work :)

---

### Post by Sophont on 2008-10-07
> **mbeierl said:**
> 
As far as those comments about pptp being broken and that being a deal-breaker goes: remember, intrepid is still in alpha, not everything is guaranteed to work :)

Intrepid *alphas* not working is not a deal-breaker of course.
It would be if the final release wouldn't work and we have to test and fix it now during this phase or it won't be ready in time.

Meanwhile I downloaded the beta and tried that - installed the pptp package and still couln't add in VPN tab (still disabled).
That was all on live CD (can't upgrade before I know VPN works).

Is a reboot required before PPTP VPN can be configured? (that's a problem with the live CD of course ;-) ).

To those above who could add VPN at all (with PPTP) - was that with repo packages - or PPA? (didn't have time to try that - and was hoping any needed changes would have made it into beta anyway - right? wrong?)

---

### Post by tact on 2008-10-07
> **Sophont said:**
> 
To those above who could add VPN at all (with PPTP) - was that with repo packages - or PPA? (didn't have time to try that - and was hoping any needed changes would have made it into beta anyway - right? wrong?)

I was just using stock intrepid repos.   I upgraded, as opposed to a clean install, and so all the packages I needed were likely already installed and were just upgraded. 

If you cannot add a new VPN connection (option greyed out) you might have to install the network-manager-pptp package first.  You can do that even in a LiveCD environment... just the install is not permanent, lost when you reboot.

I could add a new VPN connection no problem but that issue I reported above (no option to refuse-EAP) is what caused me grief.  Add in that key to gconf and PPTP VPN works fine

---

### Post by Sophont on 2008-10-08
> **tact said:**
> I was just using stock intrepid repos.   I upgraded, as opposed to a clean install, and so all the packages I needed were likely already installed and were just upgraded. 

If you cannot add a new VPN connection (option greyed out) you might have to install the network-manager-pptp package first.  You can do that even in a LiveCD environment... just the install is not permanent, lost when you reboot.

Thanks for the reply - but that part was clear. I did install the pptp package. About the only ting I can't do with the live CD system is reboot.
I have PPTP working on Hardy.

---

### Post by BARlotta on 2008-10-16
Before recent updates the refuse-eap tweak via the gconf-editor worked for me, but no longer.  Today I got another update for the network manager and now I am getting this error in the graphic instead...anyone else having any more luck with this?

"The VPN connection 'x' failed because there were no valid VPN secrets."

I do not get a dialogue asking for access to the keyring.

SysLog snippets:
```

Oct 16 18:56:01 madeye NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 16 18:56:01 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 22967 
Oct 16 18:56:01 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 16 18:56:01 madeye NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.299 (nma_vpn_request_password): canceled. 
Oct 16 18:56:01 madeye NetworkManager: <info>  Policy set 'Auto CDMA network connection' (ppp0) as default for routing and DNS. 
Oct 16 18:56:13 madeye NetworkManager: <debug> [1224197773.496990] ensure_killed(): waiting for vpn service pid 22967 to exit 
Oct 16 18:56:13 madeye NetworkManager: <debug> [1224197773.497384] ensure_killed(): vpn service pid 22967 cleaned up 
Oct 16 18:56:14 madeye NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 16 18:56:14 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 22984 
Oct 16 18:56:14 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 16 18:56:15 madeye NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.299 (nma_vpn_request_password): canceled. 
Oct 16 18:56:15 madeye NetworkManager: <info>  Policy set 'Auto CDMA network connection' (ppp0) as default for routing and DNS. 
Oct 16 18:56:27 madeye NetworkManager: <debug> [1224197787.185076] ensure_killed(): waiting for vpn service pid 22984 to exit 
Oct 16 18:56:27 madeye NetworkManager: <debug> [1224197787.185521] ensure_killed(): vpn service pid 22984 cleaned up 
Oct 16 18:58:12 madeye NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 16 18:58:12 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 23069 
Oct 16 18:58:12 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 16 18:58:12 madeye NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.299 (nma_vpn_request_password): canceled. 
Oct 16 18:58:12 madeye NetworkManager: <info>  Policy set 'Auto CDMA network connection' (ppp0) as default for routing and DNS. 

```

Edit/Update: I deleted and recreated the configuration for the VPN and I now get a keyring prompt, but I still get the same error message about no secrets...

---

### Post by tact on 2008-10-16
same prob here.  cannot get key from keyring.  try this and see if it works for you.  in the vpn configuration delete password.  leave login name there.  this way you are asked for password, it does not try to get from keyring.
 
everything seemed to work for me but the connection failed to complete ultimately (perhaps the server I ws trying to conenct to was down).

Cheers

---

### Post by BARlotta on 2008-10-16
> **tact said:**
> same prob here.  cannot get key from keyring.  try this and see if it works for you.  in the vpn configuration delete password.  leave login name there.  this way you are asked for password, it does not try to get from keyring.
 
everything seemed to work for me but the connection failed to complete ultimately (perhaps the server I ws trying to conenct to was down).

Cheers

This gets it passed the secrets problem but I still have connection issues.  Note: I also had to re-set the refuse-eap as that key was removed when I saved the changes to the password field.

```

Oct 16 19:40:48 madeye NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 16 19:40:48 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 25145 
Oct 16 19:40:48 madeye NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 16 19:40:53 madeye NetworkManager: <info>  VPN plugin state changed: 3 
Oct 16 19:40:53 madeye NetworkManager: <info>  VPN connection 'XXX' (Connect) reply received. 
Oct 16 19:40:53 madeye pppd[25152]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Oct 16 19:40:53 madeye pppd[25152]: pppd 2.4.4 started by root, uid 0
Oct 16 19:40:53 madeye pppd[25152]: Using interface ppp1
Oct 16 19:40:53 madeye pppd[25152]: Connect: ppp1 <--> /dev/pts/1
Oct 16 19:40:53 madeye pptp[25155]: nm-pptp-service-25145 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Oct 16 19:40:53 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Oct 16 19:40:53 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Oct 16 19:40:53 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Oct 16 19:40:54 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Oct 16 19:40:54 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct 16 19:40:54 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 36183). 
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Oct 16 19:40:55 madeye pppd[25152]: MS-CHAP authentication failed: E=691 Authentication failure
Oct 16 19:40:55 madeye pppd[25152]: CHAP authentication failed
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Oct 16 19:40:55 madeye pppd[25152]: Connection terminated.
Oct 16 19:40:55 madeye NetworkManager: <info>  VPN plugin failed: 1 
Oct 16 19:40:55 madeye pptp[25155]: nm-pptp-service-25145 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Oct 16 19:40:55 madeye pptp[25155]: nm-pptp-service-25145 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Oct 16 19:40:55 madeye pptp[25161]: nm-pptp-service-25145 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Oct 16 19:40:55 madeye NetworkManager: <info>  VPN plugin failed: 1 
Oct 16 19:40:55 madeye pppd[25152]: Exit.
Oct 16 19:40:55 madeye NetworkManager: <info>  VPN plugin state changed: 6 
Oct 16 19:40:55 madeye NetworkManager: <info>  VPN plugin state change reason: 0 
Oct 16 19:40:55 madeye NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Oct 16 19:40:55 madeye NetworkManager: <info>  Policy set 'Auto CDMA network connection' (ppp0) as default for routing and DNS. 

```

---

### Post by Jancis on 2008-10-17
not sure if it helps but good workaround is deleting saved password from vpn settings and entering when asked upon connection. 

it works for me then.

---

### Post by jalmargyyk on 2008-10-17
CHAP response fails for me too. Network-manager tries to send the authentication reply in a wrong format. 

```
desktop pppd[15375]: sent [CHAP Response id=0x0 <xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx>, name = "WORKGROUP\\\\jallu"]
```

The above line can be seen in syslog if debug option is enabled from /etc/ppp/options file.

Correct format would be $SERVER\\$USERNAME. Bug appeared to me something like four days ago.

I've filed a bug about this to launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/283376](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/283376)

BTW, manually making the connection works just fine (using pon command).

---

### Post by mbeierl on 2008-10-20
Woot!  I just got a NM pptp connection to my pptp-enabled conntivity firewall at work!  I had to do the "delete the password" trick again, but other than that, it's progress!

---

### Post by tact on 2008-10-20
> **mbeierl said:**
> Woot!  I just got a NM pptp connection to my pptp-enabled conntivity firewall at work!  I had to do the "delete the password" trick again, but other than that, it's progress!

Yep working for me here too provided (as per my post above):
-  have no password set in the settings to force being prompted for one manually
-  set the "refuse-EAP" key in gconf settings

---

### Post by BARlotta on 2008-10-21
> 
Yep working for me here too provided (as per my post above):
- have no password set in the settings to force being prompted for one manually
- set the "refuse-EAP" key in gconf settings 


Still not working here even with those settings.  Most likely a difference on the VPN server side.

---

### Post by Sophont on 2008-10-21
To summarize:
VPN with PPTP now works for some people, one needs to supply password *every* time and MTU/MRU in dialog still is ignored?

Sux. Sounds like it's currently still worse than what I have in Hardy atm and not much time left to release.

---

### Post by tact on 2008-10-22
> **Sophont said:**
> To summarize:
VPN with PPTP now works for some people, one needs to supply password *every* time and MTU/MRU in dialog still is ignored?

Sux. Sounds like it's currently still worse than what I have in Hardy atm and not much time left to release.

Stay with Hardy.  There is no one going to twist your arm to upgrade to intrepid the moment its gone gold.  Assess it once its released, or a few more months further down the track, upgrade only when YOU are happy to. 

Cheers

---

### Post by Sophont on 2008-10-22
> **tact said:**
> Stay with Hardy.  There is no one going to twist your arm to upgrade to intrepid the moment its gone gold.  Assess it once its released, or a few more months further down the track, upgrade only when YOU are happy to. 

Cheers

Hah - you have no idea how much I am twisting my own arm to upgrade to intrepid any minute now. ;-)
The VPN troubles are the only reason I didn't upgrade around Alpha 5.

Fun aside - regressions are bad. New features not working yet is one thing - stuff that already worked failing is quite another.

No worries in my case - 8.04 is fine - I will keep checking and not upgrade before I can verify with live CD that I can connect via VPN as I need that for my job.

But many people will upgrade on release or soon after - either because they need some fix (8.04 wasn't perfect for everybody - fresh kernel alone will fix many hardware problems) or simply because the nice upgrade button invites them to.

The introduction of a regression flag was a good idea and shows that Ubuntu devs understand that regressions need more attention.

---

### Post by BARlotta on 2008-10-22
This VPN issue is definitely a pain.
- Hardy need to use wvdial to use my 3G card which meant I couldn't use the VPN connections of NM to dial into my work network.
- Intrepid, NM now works great with my 3G card, but the VPN (pptp) does not work with my servers.

Overall, I like Intrepid a lot - I just can't wait till this issue gets ironed out.

---

### Post by houstonbofh on 2008-10-24
I so need a fix for this.  Righ now I am frozen on Gutsy enterprise wide because of the Hardy kernel freezes (among other things)  Intrepid fixes almost all my Hardy show stoppers!  But this is a big deal...

1) No passwords in the keyring.  This is an easy, but totally non-intuitive workaround.

2) Still fails to connect to a m0n0wall VPN that worked fine with default setting from Dapper to Hardy.  Kind of a big deal since I have 75 of them.

My concern is that 18 months is coming up fast, and I am still frozen on Gutsy.  I have run every version since Breeze Badger, and Hardy was the fist skip.  If I have 2 in a row, there is no more safety margin.

---

### Post by BARlotta on 2008-10-24
> **houstonbofh said:**
> I so need a fix for this.  Righ now I am frozen on Gutsy enterprise wide because of the Hardy kernel freezes (among other things)  Intrepid fixes almost all my Hardy show stoppers!  But this is a big deal...


Have you tried using pon/poff?  It is a command line interface and needs a config file(s) but it worked for me (hopefully as a temporary fix).

---

### Post by megamaced on 2008-10-25
Thought I'd throw in my two pennies worth..

I cannot get a VPN connection to work in Intrepid whatsoever. I was getting the shared secrets error but I got around that by removing my password from the settings and forcing NM to ask for it when connecting. Even so, I still cannot connect and I have tried adding the refuse-EAP option.

PPTP VPNs worked fine in Hardy and I have copied the VPN settings exactly as they are in Hardy to Intrepid but it makes no difference.

Also I noticed that the Intrepid network manager does not give a reason why it failed to connect the VPN in system log. At least with Hardy I could see why the VPN failed, ie bad password or MPPE encryption required...

I plan to stick with Hardy anyway until the next LTS. But I feel for those people that need to upgrade...

Regressions are BAD :(

---

### Post by houstonbofh on 2008-10-25
> **BARlotta said:**
> Have you tried using pon/poff?  It is a command line interface and needs a config file(s) but it worked for me (hopefully as a temporary fix).
The problem is that I need this for 100 non-technical people, and hack just are not an option.  I mean this has me seriously concerned.  If I have to stick on the Gutsy freeze, I have 6 months to fix Intrepid +1 or find another distro and **move my entire company to it!**  That will be a nightmare!

---

### Post by Dittohead on 2008-10-25
I cannot connect either. I have Hardy but have setup sources with the latest builds of network-manager.

My home network as well as the two at work all run on WPA2, which the Hardy version of network-manager doesn't connect to.

```
Oct 25 15:47:01 allworthnl NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 25 15:47:01 allworthnl NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5577 
Oct 25 15:47:01 allworthnl NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 25 15:47:14 allworthnl NetworkManager: <info>  VPN plugin state changed: 3 
Oct 25 15:47:14 allworthnl NetworkManager: <info>  VPN connection 'Work' (Connect) reply received. 
Oct 25 15:47:14 allworthnl pppd[5581]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Oct 25 15:47:14 allworthnl kernel: [  719.405774] PPP generic driver version 2.4.2
Oct 25 15:47:14 allworthnl pppd[5581]: pppd 2.4.4 started by root, uid 0
Oct 25 15:47:14 allworthnl pptp[5593]: nm-pptp-service-5577 log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Oct 25 15:47:14 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Oct 25 15:47:14 allworthnl pppd[5581]: Using interface ppp0
Oct 25 15:47:14 allworthnl pppd[5581]: Connect: ppp0 <--> /dev/pts/0
Oct 25 15:47:14 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Oct 25 15:47:14 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 41069). 
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Oct 25 15:47:15 allworthnl pptp[5597]: nm-pptp-service-5577 warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Oct 25 15:47:15 allworthnl pppd[5581]: MS-CHAP authentication failed: E=691 Authentication failure
Oct 25 15:47:15 allworthnl pppd[5581]: CHAP authentication failed
Oct 25 15:47:16 allworthnl pppd[5581]: Connection terminated.
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Oct 25 15:47:16 allworthnl NetworkManager: <info>  VPN plugin failed: 1 
Oct 25 15:47:16 allworthnl pptp[5593]: nm-pptp-service-5577 warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Oct 25 15:47:16 allworthnl pptp[5593]: nm-pptp-service-5577 warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Oct 25 15:47:16 allworthnl pptp[5597]: nm-pptp-service-5577 log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Oct 25 15:47:16 allworthnl pppd[5581]: Exit.
Oct 25 15:47:16 allworthnl NetworkManager: <info>  VPN plugin failed: 1 
Oct 25 15:47:16 allworthnl NetworkManager: <info>  VPN plugin state changed: 6 
Oct 25 15:47:16 allworthnl NetworkManager: <info>  VPN plugin state change reason: 0 
Oct 25 15:47:16 allworthnl NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
```

---

### Post by uBeer on 2008-10-27
I read all this stuff about setting up a PPP connection and I wondered because NM couldn't set up a working ppp connection for me. And I couldn't get pppoeconf to work (that works almost flawlessly on hardy, gutsy, feisty...), so I was wondering how you all get to set up a ppp connection (pppoe, don't know if it is that different from pptp)? With or without NM?

---

### Post by BARlotta on 2008-10-27
> **houstonbofh said:**
> The problem is that I need this for 100 non-technical people, and hack just are not an option.  I mean this has me seriously concerned.  If I have to stick on the Gutsy freeze, I have 6 months to fix Intrepid +1 or find another distro and **move my entire company to it!**  That will be a nightmare!

Alexander Sack just put a patch out on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168").  I haven't tried it yet.

---

### Post by houstonbofh on 2008-10-27
> **BARlotta said:**
> Alexander Sack just put a patch out on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168").  I haven't tried it yet.
Test it if you can.  It seems to work for some but not for others.

---

### Post by megamaced on 2008-10-27
> **BARlotta said:**
> Alexander Sack just put a patch out on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168").  I haven't tried it yet.

Awesome! Those packages work! I got pptp to work after deselecting everything but mschap v1. I am glad that the option to disable eap is available now. I also enabled mppe and forced 128bit and enabled stateful mode. I then deselected all of the compression options because they never worked for my in Hardy.

Cheers!

---

### Post by megamaced on 2008-10-28
ADDITIONAL: Unfortunately it seems as though the shared secrets error still appears if you try to save the vpn password...

---

