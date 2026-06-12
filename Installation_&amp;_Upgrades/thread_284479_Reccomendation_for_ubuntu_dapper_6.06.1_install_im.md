---
title: "Reccomendation for ubuntu dapper 6.06.1 install improvement"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Henry Hollenberg on 2006-10-25
Hey gang,

Did the install last night and it was very smooth and
self-explanatory on pretty whacky hardware (amd64, nvidia,
wide lcd non-VESA-standard flatscreen).  Good Work!

Noticed one thing that could be improved without much effort.

It seemed the system was trying to go out and check some standard
package mirrors during the install and it threw up a message
about not being able to get security updates.

Also saw some indian-signs in /etc/apt/sources.list that suggested
to me that the install would have automatically uncommented some
mirror sites for me had networking been configured.

I didn't set up networking as I anticipated incorrectly that 
the install would ask me to do so.

So if I am correct in all the above assumptions (might be a stretch!),
I would suggest the install offer to let the user set up
networking, with perhaps a blurb about how that would be helpful to
user before trying to check the mirror sites. There could always be an
option to proceed without setting up the networking if the user so chooses.

Just my 2 cents.  If there was a more appropriate place to post
this please let me know!

hgh.

---

