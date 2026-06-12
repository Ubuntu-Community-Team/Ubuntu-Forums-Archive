---
title: "Upgrading Past 8.04 Hardy Heron Removes Temperature from Gnome Clock"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by DjTeriyake on 2009-12-18
When I upgraded from 8.04 Hardy Heron to 9.04 Jaunty Jackalope a few months back I recall that it removed the temperature from my Gnome clock applet in the top-right side of the screen next to my username. I didn't think much of it as I installed Screenlets and ran ClearWeather. I was hoping the upgrade to 9.10 Karmic Koala would resolve this issue, but it didn't. Again, no big deal since I'm running Screenlets.

Today I just booted into an old computer of mine that still has 8.04 Hardy installed, and in the top-right there it is, the old working temperature, reminding me that all was well back in Hardy.

I've attached some screenshots to show the differences. Both versions show the correct icon for the weather, but whereas 8.04 Hardy shows the temperature, 9.10 Karmic shows blank dashes (--). Both locations are the same and are set as "Home." In configuring both versions of the applet they both predict my hometown correctly, both are set to display in Fahrenheit, both have the same timezone, etc. Everything's the same, but 9.10 Karmic refuses to show the temperature.

What's going on, and is there a fix? At times I get tired of Screenlets and turn them off so it would be nice to be able to have a quick peek at the temperature now and again. On the plus side, it's 72° in the middle of December here in southern California  8-).
[B]
8.04 Hardy Weather[/B]
[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/Ubuntu-804-Jaunty-Weather.jpg[/IMG]

**9.10 Karmic Weather**
[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/Ubuntu-910-Karmic-Weather.jpg[/IMG]

---

### Post by phillw on 2009-12-18
Hi,
> 
You must click on the top menu bar and choose Add to panel. Then choose Weather Report .
Done :smile: 		                   		  		  		 		 			 				

There,s quite a list of things you can add !!!!!

I've just added it To my test 10.04 install - so it should be working in 9.10 :-)

Regards,

Phill.

---

### Post by DjTeriyake on 2009-12-18
> **phillw said:**
> Hi,


There,s quite a list of things you can add !!!!!

I've just added it To my test 10.04 install - so it should be working in 9.10 :-)

Regards,

Phill.

Thanks Phill, but that's not working either. It shows 0° initially, then when I choose to update it shows the two dashes just like in the screenshot. To reiterate the *weather* is working fine, even when I mousover it shows the clouds, the wind, and sunrise/sunset. It's just the *temperature* that's not working. Upon mouseover the temperature is listed as "Unknown."

---

### Post by phillw on 2009-12-18
Right Click the Temperature, Select Preferences, Then the Location Tab to select the area you want.

Odd, mine is working fine - Shows Dark, a little cloud and -4 C  (It's a bit cold here in the UK !!)

Phill.

---

### Post by DjTeriyake on 2009-12-24
Still no dice. The Location tabs on both applets are set to the same location, and both applets show the correct icon for the weather, just nothing for the temperature.

Here's a screenshot of the second weather applet running and its info. It looks like it's not retrieving the weather data properly:

[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/Ubuntu-910-Karmic-Weather-Applet.jpg[/IMG]

---

### Post by DjTeriyake on 2009-12-24
OK, weird stuff going on here now. I started searching and digging for the problem, reading the myriad links on the Gnome weather bugs, etc. and I think the problem lies in the Locations.xml file that gweather uses. I *think* it's using the wrong zcode/airport data but I'm not sure. I'm mostly using the following link since it's the exact problem that I have:

[https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/404616](https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/404616)

Now, back in 8.04 Harday, I was messing around with the clock and weather config and here's what I've come up with:

 - The Gnome clock doesn't automagically predict my home town, so if I put in the latitude and longitude the weather icon is correct and the temperature works.
 - The standalone weather applet doesn't predict my home town either, nor is it in the list of cities, nor can you input your own latitude and longitude. The only thing you can do is choose the city closest to you. If I do that, the weather icon is correct but the temperature is blank.

This tells me that the two applets, though similar in function, are using different methods to access the weather. Since the clock was accessing the weather correctly, I was hoping I could switch over to Karmic and enter my own custom latitude and longitude into and the weather would work. No dice.

Now I'm hoping I can find the config file for the 8.04 Hardy clock and manually copy the settings over to my 9.04 Karmic box. That's where I'm at now...

---

### Post by DjTeriyake on 2009-12-24
The following screenshot is what I was talking about in 8.04 Hardy Heron. The clock applet gives the correct weather icon and temperature if I put in a custom location via latitude and longitude. The standalone weather applet does not have a custom location, so you have to choose the closest city, and it give a blank temperature. My next move is to copy the configuration for the 8.04 Hardy clock into the 9.10 Karmic so that hopefully the new clock will give the correct temperature:

[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/Ubuntu-Linux-804-Hardy-Clock-vs-Wea.jpg[/IMG]

---

### Post by s7726 on 2010-05-04
I have been seeing this issue ever since I updated from 8.04 (I've gone all the way up the chain, on 10.04 now). I have noticed that it will *sometimes* display the temperature late at night (not sure why that would have an affect.

But as the original poster is seeing I get the weather icon and the '--' and 'unknown' for the temperature.

---

### Post by DjTeriyake on 2010-05-16
> **s7726 said:**
> I have been seeing this issue ever since I updated from 8.04 (I've gone all the way up the chain, on 10.04 now). I have noticed that it will *sometimes* display the temperature late at night (not sure why that would have an affect.

But as the original poster is seeing I get the weather icon and the '--' and 'unknown' for the temperature.

I just did upgraded to 10.04 Lucid Lynx via a clean install, and the problem is still there. You're luckier than I, because mine will still *never* display the temperature. I hope this gets fixed, but in the meantime I'll still poke around the xml config file.

---

### Post by olayak on 2010-05-23
mine worked fine in karmic and has totally disappeared in lynx.  not even dashes!  I am in New York City, so I don't see why it should have a problem.  It registers the location, but no weather or temperature!

---

