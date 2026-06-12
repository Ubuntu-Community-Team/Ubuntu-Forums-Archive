---
title: "Breezy -&gt; Dapper upgrade failed"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by m.musashi on 2006-06-08
I'm thinking I might have to just do a clean install but if I can avoid that (or somehow copy /home files to a flash drive from a command prompt) it would be great.

I used the upgrade manager and everything seemed to be going well. However, I think my wife or kids must have turned the computer off before it finished or it failed on it's own but when I start up I get the message that x can't start (isn't properly configured) and dropped to a command line. I tried to reconfigure xorg but it didn't help. It tells me it can't find the requested screen or something to that effect.

Does that sound familiar to anyone? Easy fix? If not, how can I copy /home files from the command line to a flash drive so I can just do a clean install? Yes, I should have done that before but I was lazy. There is nothing overly important but my kids have downloaded a bunch of wallpapers and I'd like to save them if possible. If not, well, I guess it's goodbye and start over.

Thanks.

---

### Post by Fafnir on 2006-06-08
This is a *very* long shot, but you don't have an nVidia graphics card, do you? I do, and I had the same rough sort of problem (X not starting) - there's a HOWTO [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") giving details of how to reinstall the drivers. Sorry I can't be of more help.

---

### Post by m.musashi on 2006-06-08
Thanks for the help. It's a laptop with integrated graphics. I'm not real sure which one either. I just tried with the vesa driver since it almost always works but still couldn't get x to start.

---

