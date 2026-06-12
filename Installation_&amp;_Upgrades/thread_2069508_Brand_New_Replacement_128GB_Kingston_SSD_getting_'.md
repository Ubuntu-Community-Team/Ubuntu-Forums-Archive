---
title: "Brand New Replacement 128GB Kingston SSD getting 'failing' report by Disk Utility!"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-10-10
Installed this [128GB Kingston SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139950") yesterday. 
Put 64 bit 12.04 on it and it was running great yesterday! Then I shut it down for the night. I have always done this for the last 15 years.

Well today I boot up, takes 20 seconds now. After a minute disk utility sends a popup saying this new SSD is 'failing' and to back it up and replace ASAP! 

Ran the disk utility tests and all are green except for Temperature which is marked as the culprit causing this issue. 
Disk Utility said the SSD temp was 75 degrees F along with a red dot next to it!

Anyways I ran the other disk utility tests and they all passed saying drive is healthy. SSD temp was rising, now it was 90 degrees but the red light was still on the Temp section. Then after temp hit 95 degrees the 'red' temp indicator turned 'green' and Disk utility then reports all is A-OK!!! Temp stabilized at 100 degrees for the rest of the day.

Used the pc all day with no problems. SSD is fast. Faster than the < 3year old 1TB Seagate HDD that failed and was removed. So out of curiosity I shutdown the PC for supper and it remained down for a few hours. Thus allowing it to cool down completely. Then little after 9pm it was booted up again and a minute later the same popup reported the SSD was failing again by disk utility! Ran the 'Smart Data tests' which said SSD temp was 75 degrees F again like this morning, with a red light on the temp section. Then after a few minutes SSD temp rose to what it is now 100 degrees F and all is green and disk utility now reports SSD is healthy and A-OK!

Anyone have any ideas what is going on?
This is my first SSD and am not familiar at all with how they operate.

---

### Post by Wim Sturkenboom on 2012-10-11
I can't really help you (no experience with SSD either ;))

The temperature is OK and should not give an alarm. Worst case operating temperatures for consumer electronics should be in the range of roughly 10-60 degrees celsius (sorry, I don't do Fahrenheit); often the range is bigger (e.g. 0-70 degrees celsius).

How fast is a reboot once warmed up? I guess that it is a lot faster than the 20 seconds. In which case it does indicate (in my opinion) that there's something wrong.

---

### Post by cybrsaylr on 2012-10-11
Same thing happened today.
Been keeping an eye on it with Disk Utility.

Upon morning bootup Disk Utility reports SSD failing with 75°F temp and 8 minutes later it warmed up to 90°F and red light went green  reporting all is A-OK! 

Checked right now and temp is 38°C/100°F which seems to be the temp range this SSD runs at. 
It appears it takes 8 minutes to 'warm up' which I never heard of happening with SSDs!

Those low 75°F appear to set off 'out of parameter' readings that turns the red light on with Disk Utility saying SSD is failing.

---

### Post by Wim Sturkenboom on 2012-10-12
What happens when you reboot while it's warm? Fast or slow?

---

### Post by cybrsaylr on 2012-10-12
When rebooting warm, all runs well and fast.

Same thing happened this morning. 
I boot up and disk utility alert pops up in < a minute up with a red light on temp section, which reports 75°F and says SSD is failing.

Decide to watch it closely as SSD warms up.
Keep getting many pop ups from disk utility as SSD warms which kind of impedes the use of the SSD. 

I closely watch disk utility 'smart data report' refreshing it every minute since it takes about 8 minutes to warm up. Red light is on but as soon as disk utility hits 88°F it goes green and disk utility then reports SSD is now completely healthy!

Disk utility is running in the background now so I can easily check it and now reports temp is 33°C/91°F which seems to be the normal temp now.

---

### Post by piloti on 2012-10-14
Good morning....
I am having a simialr problem, except one step earlier. 

I have the same Kingston 128 SSD and am trying to install ubuntu onto a Netbook. I have Ubuntu on a USB stick.

If I "run" from the USB stick, everything seems to be ok. When I try to install I get similar "hd fail" messages to you.

Can you tell me how you managed to do the install int he first place, I may just be doing something very wrong.....

THanks

---

### Post by cybrsaylr on 2012-10-14
piloti,
All I did was watch the video that came with the Kingston SSD and followed the directions for desktop. Install went through very smoothly for desktop. Netbook may be different but I didn't do or look into that type install.


BTW...
Same thing happened this morning. 
 I boot up and disk utility alert pops up in < a minute up with a red light on temp section, which reports 75°F and says SSD is failing.
Watched disk utility 'smart data report' refreshing it every minute since it takes about 8 minutes to warm up. Red light is on but as soon as disk utility hits 88°F it goes green and disk utility then reports SSD is now completely healthy!

Maybe I will try and call the Kingston 800 help phone number tomorrow and see if they have any answer to this.

---

### Post by cybrsaylr on 2012-10-15
Phoned Kingston 800 tech # and they were very helpful. First guy didn't really know that much and said he never heard of this happening. Then he decided to get assistance from higher level techs and said he would get back to me, since he knew nothing about Linux. A couple hours later Kingston calls back. Upper level said they have heard of this before and claim it is nothing to be concerned over. They suspect Linux 'disk utility' parameters are set too tight causing these drive failing alerts to pop up for temps <88°F. They say a future firmware setting should correct this but are not sure when this may happen. In the meantime they claim there is nothing to worry about. They said if it really bothers me they would either exchange this SSD for another or give me my money back if I decide to return it.

Not really sure what to do. When SSD reaches 88°F it runs fine. SSD is noticeably faster than the OEM 3 yr old Seagate 1TB HDD that was failing and was replaced.

---

### Post by Wim Sturkenboom on 2012-10-16
> 
Not really sure what to do

I can accept the argument that 'disk utility' gives an incorrect interpretation of the temperature; I don't say it's true, but it's a possibility.

But the fact that it is slow when it is cold indicates, in my opinion, a problem with the disk. And therefore I would swap it once and after that ask for the money back and try another make.

---

### Post by cybrsaylr on 2012-10-16
> **Wim Sturkenboom said:**
> But the fact that it is slow when it is cold indicates, in my opinion, a problem with the disk.

The only reason it appears slow on boot up when it is 75°F is because of a constant barrage of 'disk utility' failing alert popups whenever you attempt doing something. These alert popups continue until SSD warms to 88°F, then popups stop and all shows green in disk utility. Those constant alert popups get in the way of doing anything smoothly.

---

### Post by Wim Sturkenboom on 2012-10-16
OK, in that case there's nothing wrong with the SSD. Temperature is fine, runs fast.

Just stop the disk utility (or uninstall it) and log a bug report on launchpad.

---

### Post by cybrsaylr on 2012-10-16
I'll keep in eye on SSD but so far it appears to run fine.

Today it was colder on initial boot 23°C / 73°F and took 10 minutes to warmup.
It appears 30°C is the threshold that will trigger the failing alerts with Disk Utility. 
Once it warms to 30°C / 88°F all alerts stop and all is green.

---

