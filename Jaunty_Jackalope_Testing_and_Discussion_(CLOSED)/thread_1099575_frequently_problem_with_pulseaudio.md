---
title: "frequently problem with pulseaudio"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-18
hi, i'm using updated version of pulseaudio ( 0.9.14-0ubuntu13 ).
Listening music, for example with banshee, every 3 or 4 tracks, i hear noise through speakers, so change track and after 2 or 3 seconds, banshee stop to sound and i have this error in syslog:

pulseaudio[31559]: cpulimit.c: Received request to terminate due to CPU overload.
pulseaudio[3328]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
pulseaudio[3328]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
pulseaudio[3328]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.

---

### Post by jmmL on 2009-03-18
Is it possible this problem can be solved by adding the user to the group "pulse-rt"?

I also have this problem, so I've added myself to the group (although none of the other two pulse* groups). Too early to tell if it's made a difference yet; will report back.

---

### Post by biasquez on 2009-03-18
with adduser user pulse-rt maybe i solved problem

---

### Post by jmmL on 2009-03-18
I'd say it's possibly less frequent. But I've definitely had sound issues at least once in the past few hours. Still, less than before.

---

