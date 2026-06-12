---
title: "No such file or directory messages during boot"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2016-05-27
I started getting the following messages (excerpt from dmesg | less) scrolling on my screen quite a while ago, and I'm wondering what is causing it and if I can fix it?

```

14.478700] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.480201] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.491746] leds_ss4200: no LED devices found
[   14.492365] systemd-udevd[469]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.505826] systemd-udevd[486]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.521494] systemd-udevd[493]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.537826] systemd-udevd[500]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.548249] systemd-udevd[504]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.557871] systemd-udevd[506]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.564311] systemd-udevd[505]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.568267] systemd-udevd[510]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.570686] systemd-udevd[514]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.575062] systemd-udevd[517]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.578292] systemd-udevd[519]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.591289] systemd-udevd[525]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.597455] systemd-udevd[522]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.599144] systemd-udevd[527]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.606193] systemd-udevd[530]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.612367] systemd-udevd[531]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.612901] systemd-udevd[533]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.621705] systemd-udevd[538]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.624409] systemd-udevd[539]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.630320] systemd-udevd[541]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.634135] systemd-udevd[543]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.637128] systemd-udevd[545]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.645660] systemd-udevd[549]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.646602] systemd-udevd[548]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.651270] systemd-udevd[551]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.656728] systemd-udevd[552]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.659653] systemd-udevd[555]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.666477] systemd-udevd[559]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.668961] systemd-udevd[558]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.671481] systemd-udevd[562]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.679183] systemd-udevd[563]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.679798] systemd-udevd[567]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.682064] systemd-udevd[568]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.688597] systemd-udevd[573]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.689245] systemd-udevd[572]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.692844] systemd-udevd[575]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.695165] systemd-udevd[576]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.705579] systemd-udevd[578]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.706354] systemd-udevd[579]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.710797] systemd-udevd[584]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.712557] systemd-udevd[585]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.715984] systemd-udevd[588]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.717600] systemd-udevd[589]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.722732] systemd-udevd[593]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.724896] systemd-udevd[592]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.729473] systemd-udevd[596]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.733121] systemd-udevd[598]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.734489] systemd-udevd[599]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.739920] systemd-udevd[600]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.740148] systemd-udevd[603]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.746938] systemd-udevd[606]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.749731] systemd-udevd[605]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.752861] systemd-udevd[609]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.757237] systemd-udevd[611]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.767580] systemd-udevd[612]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.769571] systemd-udevd[615]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.776726] systemd-udevd[620]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.784674] systemd-udevd[623]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.787010] systemd-udevd[624]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.791717] systemd-udevd[628]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.796701] systemd-udevd[626]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.802082] systemd-udevd[632]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.802837] systemd-udevd[633]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   14.926601] intel8x0: white list rate for 1028:01ad is 48000
[   15.369274] systemd-udevd[662]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.376465] systemd-udevd[659]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.398309] systemd-udevd[670]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.399615] systemd-udevd[672]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.412479] systemd-udevd[676]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.424965] systemd-udevd[682]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.435096] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.452366] systemd-udevd[687]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.474493] systemd-udevd[702]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.495537] systemd-udevd[718]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.495617] systemd-udevd[714]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.503990] systemd-udevd[719]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.511073] systemd-udevd[729]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.512410] systemd-udevd[727]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.513400] systemd-udevd[730]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.528321] systemd-udevd[738]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.531140] systemd-udevd[739]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.534581] systemd-udevd[735]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.548303] systemd-udevd[745]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.550577] systemd-udevd[746]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.555758] systemd-udevd[748]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.585604] systemd-udevd[755]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.589900] systemd-udevd[767]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.592547] systemd-udevd[754]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.609737] systemd-udevd[768]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.638382] systemd-udevd[780]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.642918] systemd-udevd[782]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.646034] systemd-udevd[779]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.705764] systemd-udevd[803]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.707230] systemd-udevd[806]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.749192] systemd-udevd[819]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.783961] systemd-udevd[820]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.800320] systemd-udevd[838]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.871398] systemd-udevd[869]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.880545] systemd-udevd[863]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.888646] systemd-udevd[875]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.904501] systemd-udevd[880]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.906740] systemd-udevd[884]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.915551] systemd-udevd[887]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.923656] systemd-udevd[892]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.924311] systemd-udevd[888]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.924889] systemd-udevd[895]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.934079] systemd-udevd[897]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.955811] systemd-udevd[902]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.956466] systemd-udevd[907]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.977581] systemd-udevd[916]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.983385] systemd-udevd[920]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   15.986934] systemd-udevd[926]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.004250] systemd-udevd[936]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.009904] systemd-udevd[931]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.019322] systemd-udevd[940]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.027165] systemd-udevd[948]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.034239] systemd-udevd[952]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.040494] systemd-udevd[960]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.057284] systemd-udevd[964]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.059269] systemd-udevd[966]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.062573] systemd-udevd[969]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.071073] systemd-udevd[974]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.109095] systemd-udevd[982]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.114902] systemd-udevd[988]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.145224] systemd-udevd[985]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.146178] systemd-udevd[1022]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.152918] systemd-udevd[986]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.166901] systemd-udevd[1029]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.176242] systemd-udevd[1028]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.190077] systemd-udevd[1005]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.193076] systemd-udevd[1038]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.196245] systemd-udevd[1039]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.202933] systemd-udevd[1034]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.208352] systemd-udevd[1035]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.212382] systemd-udevd[1046]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.219054] systemd-udevd[1048]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.221543] systemd-udevd[1042]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.225663] systemd-udevd[1049]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.230928] systemd-udevd[1054]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.232457] systemd-udevd[1056]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.234954] systemd-udevd[1052]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.246761] systemd-udevd[1058]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.248125] systemd-udevd[1059]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.254080] systemd-udevd[1044]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.257479] systemd-udevd[1061]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.262536] systemd-udevd[1063]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.264304] systemd-udevd[1064]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.268502] systemd-udevd[1068]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.269932] systemd-udevd[1069]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.271537] systemd-udevd[1067]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.285434] systemd-udevd[1072]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.292232] systemd-udevd[1066]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.300518] systemd-udevd[1071]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.306087] systemd-udevd[1074]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.306391] systemd-udevd[1079]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.308976] systemd-udevd[1081]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.310416] systemd-udevd[1082]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.327625] systemd-udevd[1084]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.332701] systemd-udevd[1086]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.332716] systemd-udevd[1085]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.334872] systemd-udevd[1087]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.335795] systemd-udevd[1088]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.338669] systemd-udevd[1089]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.338995] systemd-udevd[1090]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.340547] systemd-udevd[1091]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.343824] systemd-udevd[1092]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.346712] systemd-udevd[1094]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.347025] systemd-udevd[1093]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.348746] systemd-udevd[1095]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.350068] systemd-udevd[1096]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.354788] systemd-udevd[1097]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.354884] systemd-udevd[1098]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.356656] systemd-udevd[1100]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.358441] systemd-udevd[1101]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.361854] systemd-udevd[1102]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.362867] systemd-udevd[1103]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.363554] systemd-udevd[1099]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.364158] systemd-udevd[1104]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.370098] systemd-udevd[1105]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.370874] systemd-udevd[1107]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.371389] systemd-udevd[1108]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.373299] systemd-udevd[1106]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.378660] systemd-udevd[1109]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.379260] systemd-udevd[1111]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.383382] systemd-udevd[1113]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.383500] systemd-udevd[1114]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.385283] systemd-udevd[1115]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.386194] systemd-udevd[1112]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.388226] systemd-udevd[1116]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.391281] systemd-udevd[1117]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.392100] systemd-udevd[1118]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.429022] cfg80211: World regulatory domain updated:
[   16.429029] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.429033] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.429036] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.429038] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.429041] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.429044] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.479161] systemd-udevd[1121]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.531212] systemd-udevd[1124]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.578493] systemd-udevd[1126]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   16.961377] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   17.293996] EXT4-fs (sdc5): mounted filesystem with ordered data mode. Opts: (null)
[   17.743735] systemd-udevd[1159]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.058353] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   18.816960] systemd-udevd[1179]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.818714] systemd-udevd[1180]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.825965] systemd-udevd[1183]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.829305] systemd-udevd[1184]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.834874] systemd-udevd[1187]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.837230] systemd-udevd[1186]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.838333] systemd-udevd[1185]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   18.995331] systemd-udevd[1203]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   19.092614] usblp 1-5:1.0: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01F4
[   19.092674] usbcore: registered new interface driver usblp
[   19.093706] systemd-udevd[1205]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   19.095147] systemd-udevd[1208]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   19.412939] systemd-udevd[1211]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory
[   22.142156] init: failsafe main process (1249) killed by TERM signal
[   22.883345] Bluetooth: Core ver 2.17
[   22.883401] NET: Registered protocol family 31
```

---

### Post by vasa1 on 2016-05-27
@reut2, in future, please use CODE tags to flank terminal output. It makes the post presentable.

---

### Post by reut2 on 2016-05-27
So I did use CODE tags, and I'm not sure what point #11 has to do with my post.  DO you have any idea what is causing this output?

---

