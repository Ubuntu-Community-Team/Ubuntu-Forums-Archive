---
title: "Android SDK installation on ubuntu 12.04 64 bit"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by adwaitnd on 2012-09-25
I have been attempting to install the android SDK on by ubuntu 12.04 64 bit system for quite some time now (~ 3 months; I very much remember the first attempt on 2nd July). And very sad to say, nothing has bore any fruit.

Let me describe the situation I am presently at and also the attempts I have made to get this to work.

I am situated **behind an authenticated http proxy** at my university. And that is the only way I can get internet access with any reasonable speeds (the best i get at home on my "high speed broadband" is 15 kbps).

I have **openJDK 6** installed (using the ubuntu repositories) and after reading thru a few suggestions on various forums, also installed** ia32-libs-multiarch**.
I initially tried the method mentioned on the android site:
[http://developer.android.com/sdk/installing/index.html](http://developer.android.com/sdk/installing/index.html)

The android SDK manager fails to download any package since it cant work with an authenticated proxy. To deal with this, I tried using the **squid3 proxy** server which would act as a child proxy to my university proxy. Squid is configured to use localhost(127.0.0.1) on port 8080. This configuration works with firefox (and I'm using the same to post this message, so I know it works). It allows all http access, the other protocols are not configured.

After setting proxy to "localhost", the SDK manager does show "done loading packages" but does not show the list of packages. Only android SDK tools can be seen on the list. I tried the "force use of http" options as well but the same problem shows up.

The second route i tried was to install the SDK thru eclipse, but eclipse, when I try to install the ADK plugin, just shows "**pending...**.". I tried setting the **proxy in eclipse** first directly and later as localhost with squid3 running to get no different results.

What is wrong? Can it be solved? How do I solve it?

Some people did suggest downloading the packages from somewhere directly and then creating a sort of offline installation (I did not try this to know if it would work). But that would mean I cant ever update the packages without going thru the whole painful procedure again, so is there some way besides this?

Any help in any direction would be greatly appreciated (3 months is a very frustrating time to spend behind a single installation).

EDIT: Please assume that the bandwidth problem at home cannot be solved and is a given constrain (this is important for some other reasons). The only way would be to install the SDK through the authenticated proxy.

---

### Post by gordintoronto on 2012-09-25
It might be more productive to figure out why your high-speed broadband gives you 15 kbps. What modem and router? What ISP? How many people are sharing the connection? Are you in an apartment with lots of other wireless users around you?

If it's wireless, have you used inSSIDer to select the best channel?

I can't remember whether the SDK is available by torrent. If so, you could get it downloaded by running some overnight sessions, even at 15 kbps.

---

### Post by adwaitnd on 2012-09-26
I live in India where we are usually riped off in the name of "broadband". The bandwidth here is generally pathetic. I can download using a browser at my university. But that means the sytem cant update itself.

But coming back to the main question, why does the android SDK manager not show any packages. I am very sure my squid proxy works fine.

---

