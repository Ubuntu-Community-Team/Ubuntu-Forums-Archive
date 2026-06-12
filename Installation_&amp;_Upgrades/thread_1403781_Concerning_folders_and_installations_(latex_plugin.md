---
title: "Concerning folders and installations (latex plugin in pidgin)"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by lewin on 2010-02-10
Hello. I'm new to ubuntu and my problem is rather specific, the search didn't help.

I'm trying to install a latex plugin in pidgin, and I followed the instructions exactly as worded [here]("http://ubuntuforums.org/showthread.php?t=946607").

However, when I did the following ```

$make 
$sudo make install 

```it outputs

```

mkdir -p /home/myusername/.purple/plugins
cp LaTeX.so /home/myusername/.purple/plugins

```These are hidden folders in the myusername folder, and the .purple-> plugins folder contains a Latex.so file. Shouldn't this .so file be in /usr/lib/pidgin ?

Either way, this might not be the root of the problem, I just can't see a Latex selection in Tools->plugins in pidgin.

All the other packages installed without problems as far as I know.

By the way, why are there so many hidden folders in the myusername folder?

---

