---
title: "How to disable ipv6 in Jaunty"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by diginux on 2009-02-09
I have found out my ISP's DNS server does not like IPv6 very much.

It appears Jaunty now has ipv6 built into the kernel instead of as a module, so changing /etc/modules.d/aliases to disable ipv6 does not work.

I am wondering then, how do you disable ipv6 in Jaunty?

Thanks!
JW

---

### Post by dmizer on 2009-02-09
Rather than using alias, try this howto: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by diginux on 2009-02-09
> **dmizer said:**
> Rather than using alias, try this howto: [http://ubuntuforums.org/showthread.php?t=1065469](http://ubuntuforums.org/showthread.php?t=1065469)

That links right back to this thread?

---

### Post by dmizer on 2009-02-09
Sorry, this: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by diginux on 2009-02-10
There is nothing about Jaunty on here. Since ipv6 is built into the kernel now instead of as a module(for whatever reason), these methods won't work. I already tried them.

---

### Post by dmizer on 2009-02-10
Oh great. Back to the drawing board.

Edit:
Moved to the Jaunty testing section. You'll get more help here.

---

### Post by ronacc on 2009-02-10
from kernel 2.6.28-4 onwards ipv6 is built into the lernel and cannot be disabled globaly , I already have bug #313218 filed on this . in the meantime  you can disable it in Firefox but that dosen't help other things like other browsers or apt .

---

### Post by diginux on 2009-02-11
> **ronacc said:**
> from kernel 2.6.28-4 onwards ipv6 is built into the lernel and cannot be disabled globaly , I already have bug #313218 filed on this . in the meantime  you can disable it in Firefox but that dosen't help other things like other browsers or apt .

I added a comment to the bug as well. I hope this gets resolved soon.

---

### Post by MacUntu on 2009-02-12
Maybe the preferred fix is to talk to your ISP. IPv6 is no geek thing, they better should get ready for it.

---

### Post by olskar on 2009-02-12
> **macuntu said:**
> maybe the prefered fix is to talk to your isp. Ipv6 is no geek thing, they better should get ready for it.

+1

---

### Post by ronacc on 2009-02-12
in my case it is my router that doesn't play nice with IPV6 , I have tested this by bypassing ther router and going straight to the ethernet port on my cable modem and the problem goes away . I have already got a new router , I am just leaving this one in use to test any fix they come up with , since the router is a common brand name I suspect some others also have this situation . While everything working with IPV6 is the best solution , we should not be asking people to switch isp's ( not always possible) or buy new hardware ( the windows way ).

---

### Post by dmizer on 2009-02-12
Perhaps I'm simply missing some humor here, but I seriously doubt that purchasing new equipment and/or trying to talk ISPs into becoming IPv6 compliant should be considered reasonable solutions to this problem.

---

### Post by MacUntu on 2009-02-12
> **dmizer said:**
> Perhaps I'm simply missing some humor here
No, you are missing the word "preferred". Having a way to disable IPv6 in Jaunty might be a good thing. Talking ISP X or vendor Y into getting IPv6 ready is way better.

---

### Post by ronacc on 2009-02-12
the prefered way is not always realistic . all the vendor can do about existing hardware is sympathise and the response from my ISP about any issue is reboot your modem and then reboot your computer and on top of that when you say linux they say HUH ? and as far as switching ISP's I have 2 choices , the monopoly cable company and the monopoly phone company , tweedle dumb and tweedle dumber .

---

### Post by dmizer on 2009-02-12
> **MacUntu said:**
> No, you are missing the word "prefered". Having a way to disable IPv6 in Jaunty might be a good thing. Talking ISP X or vendor Y into getting IPv6 ready is way better.

Preferred implies a second option. In this case, there is no other option other than to use an OS which does not mandate IPv6.

---

### Post by MacUntu on 2009-02-12
> **dmizer said:**
> Preferred implies a second option. In this case, there is no other option other than to use an OS which does not mandate IPv6.
That makes three options:
A. Allow to disable IPv6 in Ubuntu.
B. Use a different OS.
C. Make the world a better place.

---

### Post by diginux on 2009-02-12
> **MacUntu said:**
> Maybe the preferred fix is to talk to your ISP. IPv6 is no geek thing, they better should get ready for it.

Because AT&T is so well known for listening to their customers input :P

---

### Post by scaine on 2009-02-12
When you say "doesn't play nice", what do you mean?

I've noticed that my Jaunty box has a good two/three second pause before loading a web page.  I remember in 2005 when I first came onto the Linux scene, Mepis had a similar issue, the solution to which was to disable IPv6.

If this is the issue though, I'd be confused - my router (a Draytek 2820n) is brand spanking new and Virgin Media here in Scotland are pretty up to date - fibre backbone and 20Mb domestic connections.  Not that fibre implies IPv6 infrastructure, but still.

It would be nice to really nail this to IPv6, then we can raise a bug.

---

### Post by ronacc on 2009-02-12
there is more than one issue possible with IPV6 , in my case as I said I can pin it on my router , in other cases it may be your ISP or any other dns server in the path . about the only thing you do is try different ways to isolate where the delay is occuring , there are instructions in one of the threads here about how to ping to help isolate it , I didn't have to go that far , just bpassing the router did the deed for me , and my delay was more like 30sec to infinity .

---

### Post by scaine on 2009-02-12
Well, I'm asking because my Intrepid laptop is fine, while my nearly identical Jaunty laptop (and my Jaunty PC) suffer this DNS lookup delay thing which was atributed to IPv6 all those years ago.  Their fix worked too - blacklist the IPv6 module.

Honestly, a desktop O/S just doesn't need IPv6 enabled by default.  Seems a strange decision to me.

---

### Post by ronacc on 2009-02-12
just for grins if you are using firefox as your browser try a different browser , there have been some reports about firefox being slow in jaunty , also you can disable ipv6 in firefox try that even though your isp and router are ipv6 capable .

---

### Post by Nullack on 2009-02-13
Thats an important bug youve found ronacc, good stuff

---

### Post by scaine on 2009-02-14
Nice one Ronnac : in Firefox 3, I used about:config, then typed IPV6 into the search box.  Only one result came back - "Disable IPV6 DNS lookups" which defaults to FALSE.

Double click on that sucker, and it's nice and fast again.

Doesn't fix Synaptic though, although that's minor since it generally only has one or two domains to lookup against before kicking off the downloads.

Any ideas about what package to launch a bug against?

[EDIT : Bug already exists : [https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218]](https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218])

---

### Post by vishalrao on 2009-02-15
I'd earlier posted a thread mentioning trying sysctl to set ipv6 options which didn't seem to work...

---

### Post by justinlindh on 2009-02-19
I'm noticing in my 64-bit Jaunty install that I'm sporadically getting some host name lookup errors finding a local network host... could this be related to ipv6 being enabled? For example, I often get the following output from a Java app (and I've noticed it once when trying to ssh to a host, too, though that obviously had different output):
Exception: java.net.UnknownHostException: <servername>

---

### Post by KhaaL on 2009-02-22
> **justinlindh said:**
> I'm noticing in my 64-bit Jaunty install that I'm sporadically getting some host name lookup errors finding a local network host... could this be related to ipv6 being enabled? For example, I often get the following output from a Java app (and I've noticed it once when trying to ssh to a host, too, though that obviously had different output):
Exception: java.net.UnknownHostException: <servername>

its funny you mention this because i got it too when i tried out kubuntu 64 bit! my ISP directed me to a red site with a big white text and put me into "time out" mode for 5 minutes :lolflag:

i wonder though if its something with us running 64 bit...?

---

### Post by vishalrao on 2009-02-22
they are playing with ipv4/6 settings i believe which might be causing issues, so i guess we should report any problems in a bug, see [https://lists.ubuntu.com/archives/jaunty-changes/2009-February/005701.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/005701.html)

will search and post an email from colin watson mentioning the bug number we should post in...

edit: this might be related: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-February/007151.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-February/007151.html)

---

### Post by ronacc on 2009-02-22
the fix he mentions in the link you provided is reported to fix the ISP part of the problem but it does not cure my router problem .

---

### Post by KillerBOB on 2009-04-08
I have the same problem with my router (cheap-ish TP-LINK WR641G), where internet gets slow and some webpages doesn't even load. This goes for both Firefox and Opera and Lynx, and maybe not surprisingly in a VirtualBox Win XP.

The solution for me was to compile a new kernel with everything 'ipv6' disabled.

---

### Post by jblackhall on 2009-04-14
Fix: [http://ubuntuforums.org/showpost.php?p=7059555&postcount=24](http://ubuntuforums.org/showpost.php?p=7059555&postcount=24)

---

### Post by ronacc on 2009-04-14
i tried adding ipv6.disable=1 to my bootline in 2.6.29-rc6 and as soon as the boot starts it returns unknown option  ipv6.disable ignoring .

---

### Post by ikama on 2009-04-15
Hi all,

just for your info:

echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

is the right path of "disable_ipv6".

Not only it have solved my issues with DNS-Lookup- also my Wireless Card Intel 3945ABG now rocks!

FYI!!!

---

### Post by -jay- on 2009-04-15
> **ikama said:**
> Hi all,

just for your info:

echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

is the right path of "disable_ipv6".

Not only it have solved my issues with DNS-Lookup- also my Wireless Card Intel 3945ABG now rocks!

FYI!!!

 so what do u ad or change???

---

### Post by zika on 2009-04-15
> **-jay- said:**
> so what do u ad or change???
either add```
ipv6.disable=1
```to Your kernel line (in which case You do not have /proc/sys/net/ipv6/ directory) or do ```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```once You've finished boot.

---

### Post by bigo72 on 2009-04-16
it not works for me: Permission Denied! with "sudo" also, and also logging as root, so....
It's impossible to modify that file :-(

---

### Post by FuturePilot on 2009-04-16
> **bigo72 said:**
> it not works for me: Permission Denied! with "sudo" also, and also logging as root, so....
It's impossible to modify that file :-(

Try
```
echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6
```

---

### Post by bigo72 on 2009-04-16
nothing done again, no errors returned, but that f*****g [autocensored] file remains the same. 
ehi guys, a long time ago whe had the ownership of our machines....it's becomning pretty-microsoftly closed ..... :D

---

### Post by ronacc on 2009-04-16
I will confirm that what futurepilot says , his sugestion does create the file . zika's sugestion gave me a permission denied also .

---

### Post by dmizer on 2009-04-16
> **ronacc said:**
> I will confirm that what futurepilot says , his sugestion does create the file . zika's sugestion gave me a permission denied also .

Type
```
sudo su
```
Enter your password.

Copy/paste this command:
```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```
Check to make sure the file has changed:
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

If it has, type:
```
exit
```

---

### Post by slashdotfx on 2009-04-16
maybe you could add post-up in /etc/network/interfaces to delete the ipv6?
I've read somewhere in the web, you could delete the ipv6 interface, like

ifconfig eth0 inet6 del fe80::219:dbff:fe65:f3de/64

---

### Post by dmizer on 2009-04-16
> **slashdotfx said:**
> maybe you could add post-up in /etc/network/interfaces to delete the ipv6?
I've read somewhere in the web, you could delete the ipv6 interface, like

ifconfig eth0 inet6 del fe80::219:dbff:fe65:f3de/64

This might work in Hardy, but Jaunty handles networking in userspace via network-manager.

---

### Post by bigo72 on 2009-04-17
> **dmizer said:**
> Type
```
sudo su
```
Enter your password.

Copy/paste this command:
```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```
Check to make sure the file has changed:
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

If it has, type:
```
exit
```
It's exactly what I've done! ;-) without results.
Anyway, I published the "[dirty solution]("http://www.bigo72.com/05/04/2009/ubuntu-904-beta-jaunty-jackalope-su-eeepc-900/")" (you can translate the blog with the bottom-left widget)

---

### Post by Claus7 on 2009-04-22
Hello,

I read the entire thread and I have to say that I face problems only with opera at the moment. Firefox is working as it should.

I had problems with hardy too, yet at the beginning both of these browsers was working nicely. Disabling ipv6 I was able to have back both browsers.

I will try not to mess with kernel configurations just to have opera working. Maybe the 10th version of opera will fix that?

Regards!

---

### Post by ronacc on 2009-04-22
I've been running Opera 10 beta for awhile now and it does not have the option to disable ipv6 like FF does .

---

### Post by Claus7 on 2009-04-22
Hello,

> **ronacc said:**
> I've been running Opera 10 beta for awhile now and it does not have the option to disable ipv6 like FF does .

so you say that even without having to disable ipv6, opera 10 (alpha and not beta at the time of writing) is working nicely to you? 
I do not think that it is a matter of disabling it or not (firefox seems to work ok with it), yet how opera can behave with this enabled, at least this is what I think. Prior versions than the 10th of opera do not seem to get along very well with ipv6.

Regards!

---

### Post by ronacc on 2009-04-22
yes opera 10 works fine without ipv6 being disabled UNLESS your isp or router does not support ipv6 in which case ANY app that accesses the net would have problems unless they could be configured ( like firefox ) not to use it .

---

### Post by Claus7 on 2009-04-22
Hello,

> **ronacc said:**
> yes opera 10 works fine without ipv6 being disabled UNLESS your isp or router does not support ipv6 in which case ANY app that accesses the net would have problems unless they could be configured ( like firefox ) not to use it .

thank you very much for the info. I will expect opera 10 to arrive then.

Regards!

---

### Post by Brandon Williams on 2009-04-22
Are people looking to disable ipv6 because they are having trouble related to ipv6?

There was a bug related to ipv6 dns lookups, but a fix has been submitted and is in the current Jaunty RC. If you do not have any interfaces with global ipv6 addresses on them, glibc should be skipping the ipv6 lookup, which should result in firefox, etc. working correctly without having to do anything to disable ipv6. If there are still outstanding ipv6 related issues that can only be resolved by disabling ipv6, it would be helpful if people would open bugs related to the ipv6 issues ... not simply look for ways to disable ipv6.

We do not want new users to give up on Ubuntu due to these types of problems, and I don't think it's reasonable to expect a new user to be able to figure out that ipv6 is the problem and then figure out how to disable it.

---

### Post by ronacc on 2009-04-22
we weren't looking to disable IPV6 because we hate it, of course we were having problems with it . thats why there are posts and threads all over the forums telling people how to disable it (prior to kernel 2.6.28-4 where it was built in rather than loaded by module).I am still checking to see if the "fix" has permenently resolved the issue for me.

---

### Post by dkruidhof on 2009-04-23
I am looking to disable ipv6 because I have a big problem with it. I can't connect to my router to get online. The debug log says it is because it cannot find any ipv6 routers. Although this problem is causing me to hate it a bit. If anyone knows some way around that without disabling ipv6, then that would be great too.

---

