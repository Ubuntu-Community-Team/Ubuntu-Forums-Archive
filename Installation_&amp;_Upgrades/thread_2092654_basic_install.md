---
title: "basic install"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Vinger on 2012-12-08
Hello,

I installed today the core version of lubuntu, to have a really minimal installation.

I was wondering if there exists even a more minimal installation. I mean: ubuntu based, but only the kernel, basic applications (fe apt) and a GUI... 

Already thanks.

---

### Post by ibjsb4 on 2012-12-08
You could take it down one more notch by not installing recommends.

```
sudo apt-get install --no-install-recommends lubuntu-core
```

Or you could just build.  Display manager + window manager + a few programs.  Something like this:

```
sudo apt-get install lightdm openbox lxterminal synaptic
```

---

### Post by snowpine on 2012-12-08
There's an excellent how-to here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by TheFu on 2012-12-08
Sure. You'd install ubuntu server (minimal, nothing added), then install the exact GUI that you want - probably** fvwm** since anything else would bring lots more stuff that you want to avoid.  Even fvwm would bring in all the X/Windows, which is pretty bloated, but a necessary evil to have any GUI on Linux.

Fvwm is a pure window manager, not a desktop environment. I'm still at a loss for why DEs became popular when all that I see them providing is a bunch of stuff that hardly anyone uses anyway.  You can find sample .fvwmrc files which show how to setup the WM to your specific needs. These are simple to edit text files which describe all the menus that you want to have. The default menu is enough to do a few things that most people need - just click anywhere on the desktop to see the menus - left, right or center mouse clicks brings up different menus.  Some example fvwm desktop screenshots will probably make you more interested. [http://www.fvwm.org/screenshots/desktops/](http://www.fvwm.org/screenshots/desktops/) has some. The first page (just 5) tend to be boring. The really cool ones come later and are extremely impressive.  FVWM has been around since the mid-1990s. It isn't going anywhere.

There are lots of different window managers - LXDE uses openbox, before loading the LX-desktop environment on top. You can just run openbox along, without any DE too.

---

### Post by snowpine on 2012-12-08
> **TheFu said:**
> Sure. You'd install ubuntu server (minimal, nothing added)...

Desktop/laptop users should **not** install Ubuntu Sever. Ubuntu Server is for, well... servers.

---

### Post by ibjsb4 on 2012-12-08
Yep, you can go with the mini.iso or ..

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

---

### Post by TheFu on 2012-12-08
> **snowpine said:**
> Desktop/laptop users should **not** install Ubuntu Sever. Ubuntu Server is for, well... servers.

Why not?  References please.

I found this [https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F) which says that there is not anything different at the kernel level between desktop and server versions.

I've been doing this for about 4 yrs and I'm much, much happier. It is the easiest way to avoid most of the things I consider bloat that Ubuntu Desktop has become while keeping the best parts of Ubuntu (APT, stability, reasonably current apps).

---

### Post by snowpine on 2012-12-08
> **TheFu said:**
> Why not?  References please.

I've been doing this for about 4 yrs and I'm much, much happier. It is the easiest way to avoid most of the things I consider bloat that Ubuntu Desktop has become while keeping the best parts of Ubuntu (APT, stability, reasonably current apps).

I recommend the tutorial I linked to in post #3.

If the goal is to avoid unnecessary packages, Ubuntu Server will install a whole bunch of stuff the average desktop/laptop user doesn't want/need, such as apache, php, mysql, etc. and furthermore I believe Server has a different kernel that is "tuned" for server tasks, not desktop/laptop/netbook performance. (although my knowledge might be a little outdated since I haven't used Ubuntu much in several years)

---

### Post by Cheesemill on 2012-12-08
> **snowpine said:**
> If the goal is to avoid unnecessary packages, Ubuntu Server will install a whole bunch of stuff the average desktop/laptop user doesn't want/need, such as apache, php, mysql, etc. and furthermore I believe Server has a different kernel that is "tuned" for server tasks, not desktop/laptop/netbook performance. (although my knowledge might be a little outdated since I haven't used Ubuntu much in several years)
Not true. A minimal server installation won't have anything on it that you don't choose. Apache and everything else you mentioned are optional extras that you can choose if you want to.

Also the Desktop and Server versions now use identical kernels as well.

For a package and memory comparison for the different minimal installs check out my post [here]("http://ubuntuforums.org/showpost.php?p=12156448&postcount=10").

---

### Post by ibjsb4 on 2012-12-09
Server vs mini.iso; inquiring minds want to know  :)  So I loaded them both up and ..

[ATTACH]228444[/ATTACH]

[ATTACH]228445[/ATTACH]

---

### Post by Cheesemill on 2012-12-09
> **ibjsb4 said:**
> Server vs mini.iso; inquiring minds want to know  :)  So I loaded them both up and ..

You can get around 40 less packages installed from the Server ISO if you hit F4 on the first screen and select 'Install a minimal system' (or around 160 less if you go for the VM install).

See the link in my post above for more details.

---

### Post by ibjsb4 on 2012-12-09
> **Cheesemill said:**
> You can get around 40 less packages installed from the Server ISO if you hit F4 on the first screen and select 'Install a minimal system' (or around 160 less if you go for the VM install).

See the link in my post above for more details.

I did not even see that link!  But got to say NICE.

Now to figure out why a VM install drops so many packages :confused:

---

### Post by Cheesemill on 2012-12-09
> **ibjsb4 said:**
> I did not even see that link!  But got to say NICE.

Now to figure out why a VM install drops so many packages :confused:
A VM install is the absolute bare minimum amount of packages needed for a bootable Ubuntu system, because it is designed for creating your own VM appliances it comes without most of the things you would expect from an installation (man pages being a notable example).

---

