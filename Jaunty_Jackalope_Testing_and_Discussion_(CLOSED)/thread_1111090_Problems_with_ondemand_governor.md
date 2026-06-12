---
title: "Problems with ondemand governor"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-03-30
I've recently become concerned that something isn't quite right with cpu scaling on my laptop. By default, the governor is set to "ondemand", but often it seems that it doesn't respond to increasing cpu loads.

I am using the panel applet to change the governor, and the applet has the necessary permissions to be able to do this. It is reproducible in this way:


[LIST=1]
[*]Set the governor to ondemand
[*]View the video located here [http://vimeo.com/3711284](http://vimeo.com/3711284)
[*]Observe any stuttering due to dropped frames
[*]Set the governor to the highest frequency (in my case 1.67GHz)
[*]I now notice that no frames are dropped
[*]Set the governor to the lowest frequency
[*]Notice that frames are being dropped again
[/LIST]

I also notice that during playing the video with the ondemand governor set that the frequency does not increase from 1GHz.

I am viewing the videos using firefox-3.5, but also experience the same problems using firefox-3.0.8. I have a Intel Core 2 Duo T5450 which is capable of 1, 1.33 and 1.67 GHz frequencies.

Is this just due to problems with flash, or is it something more than this?
I don't notice frame dropping in mplayer (even when restricting decoding to a single core), but mplayer has always been much more efficient than any flash-based player.

Can anyone shed light on this?

---

### Post by manuelb on 2009-04-08
I've the very same problem and i'm running on an AMD64 Athlon X2 processor and an nVidia 9400GT with everything else running really fine (latest Ubuntu Jaunty w/ updates).
This isn't the only problem for me: i also notice mouse hovering in dropdown combobox lists in Firefox, tab switching and jquery slide animations.. everything is pretty slow until i manually change the cpu governor to "performance" from "ondemand".
It seems to me the **/sys/devices/system/cpu/cpu<n>/cpufreq/ondemand/up_threshold** isn't very effective since hardly a jquery animation can take 95% of the processor on multicore CPUs for the time needed for the governor to raise the frequency.
As i'm trying to looking into this, i found out quite good results in lowering this threshold to something like 20:

```
echo 20 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
echo 20 | sudo tee /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold
```

Now i'm looking for a reliable way to do this at startup time since there is an /etc/init.d/ondemand script that seems to set the "ondemand" governor after 60 seconds but i can't get it to work via sysfs or rc.local.. any ideas?

[update]

FYI, i modified my **/etc/init.d/ondemand** script to set a lower **up_threshold** value, here is the snippet:

```

...

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done

	for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 20 > $CPU_THRESHOLD
	done
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

I just added the **for CPU_THRESHOLD** section and it will do the work: i don't like this solution since i think there should be a good reason behind that 95.. anyone can explain that?

---

### Post by manuelb on 2009-04-08
Btw, i wonder what governor Windows XP is using.. i mean, "ondemand" with up_threshold of 20 is still somewhat "slow" in catching up the cpu load and most of the high-intensive operations that could appear on a web page are cpu-bound for a small slice of time, ie an autoscrolling element on a webpage that scroll the content once every 4/5 seconds, in this case the "ondemand" governor fails miserably :mad:
I tried hacking the sampling_rate value but to no avail.

---

