---
title: "Virtual Ubuntu up, but no internet"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by ibexslam on 2012-06-20
I don't seem to be able to get my virtual Ubuntu hooked up to the internet...there's no internet access.

I've tried changing Virtualbox's Settings > Network settings. Did not seem to help. "Enable Network Adapter" is ghost-checked and not changeable.

I "allowed" VirtualBox under Windows' firewall control. This also does not seem to have made a difference.

I'm running Ubuntu 12.04 using VirtualBox 4.1.16 on Windows 7 running on a desktop machine. There's no problem with the host machine accessing the internet. Just the guest.

Any tips on what to tweak?

Thanks!

I.

---

### Post by mastablasta on 2012-06-21
in windows you can see your networks and then check what kind of settings vbox has. in xp it's in control panel in network connections or something like that.

---

### Post by Grenage on 2012-06-21
> **ibexslam said:**
> I don't seem to be able to get my virtual Ubuntu hooked up to the internet...there's no internet access.

I've tried changing Virtualbox's Settings > Network settings. Did not seem to help. "Enable Network Adapter" is ghost-checked and not changeable.

I "allowed" VirtualBox under Windows' firewall control. This also does not seem to have made a difference.

I'm running Ubuntu 12.04 using VirtualBox 4.1.16 on Windows 7 running on a desktop machine. There's no problem with the host machine accessing the internet. Just the guest.

Any tips on what to tweak?

Thanks!

I.

It's been a while since I've used Vbox, but there should be a network adapter mode of 'NAT' available on the client.  The client may need to be turned off when you make the change.

I have a sneaking suspicion that I actually used 'bridged mode' when I dabbled with vbox.

---

### Post by darkod on 2012-06-21
Both NAT mode and Bridged mode should work, there is only a slight difference in the result.

Sometimes with 12.04 I have seen DNS issues, so first check where is the problem.

Boot the client (ubuntu), open terminal and try:
ping 8.8.8.8

If that returns a result, you have internet access (you stop the command with Ctrl + C if you don't know that).

Then try:
ping [www.google.com]("http://www.google.com")

If that doesn't work, and it worked with the IP above, it's only a DNS issue.

Click on the Network Manager icon (top right), Edit Connections, select the connection and the button Edit.

Click on the IPv4 tab, and change from Automatic to Automatic IP Only, or something like that.
In the DNS field below enter your ISP DNS servers, or use the google DNS which is 8.8.8.8.

Close all of that. It will save the change.

Now you should have full internet access.

---

### Post by ibexslam on 2012-06-21
Darkod,

That did it.

As you suspected, the first ping worked, and the second did not.

On the IPv4 tab, I changed "Method" to "Automatic (DHCP) addresses only" and "DNS Servers" to 8.8.8.8 .

And, just like that, the problem went away.

Thank you! Much obliged!
I.

---

