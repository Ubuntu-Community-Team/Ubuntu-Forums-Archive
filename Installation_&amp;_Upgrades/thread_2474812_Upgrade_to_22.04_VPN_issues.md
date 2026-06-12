---
title: "Upgrade to 22.04 VPN issues"
date: 2022-05-09
forum: Installation &amp; Upgrades
---

### Post by drjdmartin on 2022-05-09
Hi,

I'm having issues with starting an RDP session to my work computer post upgrading to Jammy. It looks to be to do with the TLS as I'm getting the following errors from freerdp:

```
 [12:15:44:973] [13830:13831] [ERROR][com.freerdp.core] - transport_connect_tls:freerdp_set_last_error_ex ERRCONNECT_TLS_CONNECT_FAILED [0x00020008] 
```

and Remmina says "Could not connect to the RDP server ... via TLS. See the DEBUG traces for more information", but running in a terminal doesn't give too many clues.

Some quick Googling suggests it may be to do with the fact that the current version of OpenVPN might have a harder TLS criteria that does not cater for my firms old protocol for TLS (see this thread [https://ubuntuforums.org/showthread.php?t=2471455](https://ubuntuforums.org/showthread.php?t=2471455)). How can I confirm this, and is there a way of manually configuring the freerdp connection to accept a lower standard if so?

Your help is appreciated.

Thanks,

James

---

### Post by TheFu on 2022-05-09
There are LTS checking tools which will test for all versions and report which the server allows.  The one I've used is a github project and needed some manual setup and libraries installed at the time. **testssl**.  I used it once for about 30 minutes which was sufficient for my needs. [https://github.com/drwetter/testssl.sh](https://github.com/drwetter/testssl.sh)  Appears they've kept moving forward, so it could be different now.

Be certain to read the release notes for RDP support in 22.04. Some things seem to have changed. I don't use RDP, so only have a vague memory of the mention.  

I haven't tried to move my openvpn server to 22.04.  After all, *new is the enemy of stable*.  To avoid fighting as many issues as possible, I try NOT to be an early adopter. Figure I did my EA time in the 1990s for many years.

---

### Post by drjdmartin on 2022-05-09
Thanks for your response - just to be clear I'm just trying to open a client session on Ubuntu to connect to my workplace's network. The VPN will connect with no issues but trying to connect to the remote server using FreeRDP / Remmina is throwing the error. I'd be a bit worried running that script on my work's connection in case it looks like hacking.

From the release notes openssl looks to have gone through a major change which has disabled some legacy functionality so perhaps that is the root cause of the issue.

---

### Post by TheFu on 2022-05-09
Can you test FreeRDP / Remmina from inside the LAN while at work?
[B]Simplify and test. Repeat.
[/B]That's the standard method to narrowing down issues.

---

### Post by drjdmartin on 2022-05-09
In principle I probably can but I'll need to install Jammy on a one of my other laptops that are decent enough as I'm only running it from a desktop at the moment. My linux laptop I have lying around is 32 bit and runs debian 10! I'll let you know if I'm able to do this test.

EDIT: Actually maybe I can't - I think even inside work I'd need to go via the VPN on a personal device

My workaround at the moment is just to run another OS (Windows 10) in Virtualbox with a bridged network adapter and connect using that.

---

### Post by TheFu on 2022-05-09
I bet the VPN guys would like to help figure this out.  I was a corporate VPN guy. We deployed specific infrastructure to support 5K concurrent connections for 25K people all using 2FA and were interested primarily in getting the work-provided systems to work, but a few of the security team members refused to run Windows.  They had patents and the SVP over them made allowances. Anyway, the security guys had to review and sign-off on any remote access designs, then they'd perform penetration tests before we went live.  The SecurID team was an extension of IT-Sec, so any changes to the system were known to them all and carefully considered.

Our 150K servers where ¾ Unix and ¼ Windows, so we had in-house Unix expertise. If you are in a Windows-shop, I'm so sorry. You are probably screwed unless you know someone in IT or Security doing Linux stuff. It is possible they've already solved the issue.

The trick was to come to them seeking help to accomplish it the right way. They want to help, provided it is interesting and doesn't cost money and they aren't too slammed with work.  That's pretty much human nature.

In financial businesses, I could understand being hostile towards non-MSFT desktop support.  Those companies usually have all sorts of mandates for end-users.

---

### Post by drjdmartin on 2022-05-10
Thanks - yes I think you are right, I'll certainly share the problem with them to chew the cud!

As usual the there are some pros and cons to things breaking. Because I'm having to use Virtualbox it's really put the boot into using using Barrier to share the desktop across two computers. So I'm just using Remmina to remote into the 2nd computer. This means I can switch to Wayland and see how that performs (Barrier doesn't work with Wayland).

EDIT: Virtualbox with multi monitors doesn't seem to work very well with Wayland either, I experienced freezes, so I'm back to Xorg.

---

### Post by troffasky on 2022-05-23
I am also seeing these ERRCONNECT_TLS_CONNECT_FAILED errors post-upgrade. I cannot connect to my employer's servers, but I can connect to a customer's systems. 
Windows 2012 and 2016 are in use on both networks so I assume this is something to do with level of security configured in the domain, not specifically the target OS version.

---

### Post by troffasky on 2022-05-23
This is logged server-side when it fails:

> An TLS 1.2 connection request was received from a remote client application, but none of the cipher suites supported by the client application are supported by the server. The SSL connection request has failed.
and

> A fatal alert was generated and sent to the remote endpoint. This may result in termination of the connection. The TLS protocol defined fatal error code is 40. The Windows SChannel error state is 1205.



Inevitably it doesn't say what was offered by either side...

---

### Post by troffasky on 2022-05-24
If I pass  /tls-seclevel:0 to xfreerdp then it works but this sounds like some kind of security downgrade to me!

---

