---
title: "Conky looks weird after upgrade 18.10 to 19.04"
date: 2019-04-24
forum: Installation &amp; Upgrades
---

### Post by johnzondag on 2019-04-24
Hi,

I had a nice conky script that showed information in the right-hand corner and was transparent. After upgrading from 18.10 to 19.04
- the background is black
- the refresh is not working, new information like top processes is written over the existing information without clearing it

Any ideas?

---

### Post by subs05 on 2019-04-25
I changed the following line in .conkyrc from:
> own_window_transparent yes 
to 
> own_window_transparent no

This made it usable again, but I'd prefer being able to leave it transparent.

---

### Post by johnzondag on 2019-04-27
Thanx for the tip, at least it is workable now. But I also prefer it the way it was and I hope there will be another answer or a fix soon.

---

### Post by DuckHook on 2019-04-27
Ubuntu (as well as almost all distros) is in the process of transitioning from X11 to Wayland. Conky scripts are expected to be major ongoing casualties, even where X11 is still used. X11 maintenance is falling by the wayside and bugs/regressions are taking longer to fix (if at all).

One of the longest-running and most active threads on the forums is [this Conky thread]("https://ubuntuforums.org/showthread.php?t=281865"). It contains a wealth of info re fine-tuning Conky scripts, although I doubt that it's gotten to Wayland yet. Definitely worth examining, though be prepared for a long read. Please use good netiquette if posting, as it is called "best Conky screenshots" and not "help with Conky scripts", though the two topics are obviously somewhat related.

Remember that, if asking for technical help, to do so in the technical subforums.

---

### Post by again? on 2019-04-28
Testing with nvidia drivers in 19.04, I can resolve the problem by using real transparency...**own_window_argb_visual**
For latest configs use...
```
own_window_argb_visual = true,
own_window_argb_value = 0,
```

For old configs use ...
```
own_window_argb_visual yes
own_window_argb_value 0
```


****Note:** If you want a semi-transparent window also turn off fake transparency.
New config... 
```
own_window_transparent = false,
```

Old config...
```
own_window_transparent no
```

Then set your "own_window_argb_value". 
Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.

[[img]https://cdn.scrot.moe/images/2019/04/28/12-20-31.th.png[/img]](https://www.scrot.moe/image/aRPIv) [[img]https://cdn.scrot.moe/images/2019/04/28/12-21-41.th.png[/img]](https://www.scrot.moe/image/aRYAY)

---

### Post by trekerj on 2019-06-09
I'm having the same problem after upgrading. The transparency was fine for a while but has suddenly gone to a black background. I am using true transparency
Here is my config. Would appreciate any thoughts.

```
conky.config = {
    
    update_interval = 1,
    cpu_avg_samples = 2,
    net_avg_samples = 2,
    out_to_console = false,
    override_utf8_locale = true,
    double_buffer = true,
    no_buffers = true,
    text_buffer_size = 32768,
    imlib_cache_size = 0,
    own_window = true,
    own_window_type = 'normal',
    own_window_argb_visual = true,
    own_window_argb_value =0,
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    border_inner_margin = 5,
    border_outer_margin = 10,
    -- xinerama_head = 1,
    alignment = 'bottom_right',
    gap_x = 0,
    gap_y = 33,
    draw_shades = false,
    draw_outline = true,
    draw_borders = false,
    draw_graph_borders = true,
    use_xft = true,
    font = 'Ubuntu Mono:size=12',
    -- xftalpha = 0.8,
    uppercase = false,
    default_color = 'yellow',
    own_window_colour = '#000000',
    minimum_width = 300, minimum_height = 0,
    alignment = 'top_right',
    
    };
```

---

### Post by again? on 2019-06-09
Using your config, transparency works for me in up to date 19.04 with nvidia or nouveau gfx drivers.
Try restarting conky ....
```
killall -SIGUSR1 conky
```

Also check in a new user account to eliminate residual configs.

---

### Post by trekerj on 2019-06-10
Tried your suggestion, but no joy.  Thanks for checking the conky, it must be some issue I have with a desktop setting.

---

### Post by again? on 2019-06-10
Check your gfx drivers.
```
lspci -k | grep -A3 VGA
```

---

