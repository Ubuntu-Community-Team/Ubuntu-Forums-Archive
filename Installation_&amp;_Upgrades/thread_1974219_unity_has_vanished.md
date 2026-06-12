---
title: "unity has vanished"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by slgtheindividual on 2012-05-05
**unity has vanished** 			
 			 			 		   		 		 		no idea why, I logged in and the top and side panels are just completely gone, I was running unity 3d with no problem.

running "unity" from a terminal gives me:


$ unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object  file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object  file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared  object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object  file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing snap options...done
Initializing place options...done
Initializing session options...done
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open  shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so'  : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so'  : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared  object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared  object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so'  : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so'  : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so'  : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object  file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object  file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin  '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared  object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key




any help would be greatly appreciated =]

---

### Post by wilee-nilee on 2012-05-05
You can reset unity to the install state, go alt-f2 and type in unity --reset

---

### Post by slgtheindividual on 2012-05-06
> **wilee-nilee said:**
> You can reset unity to the install state, go alt-f2 and type in unity --reset


I tried this and I got the output 
```

WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e00011

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x30000b8

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...[ERROR]: Option "toggle_window_key" already defined
[ERROR]: Option "toggle_screen_key" already defined
[ERROR]: Option "switch_filter_key" already defined
[ERROR]: Option "filters" already defined
[ERROR]: Option "filter_decorations" already defined
[ERROR]: Option "filter_match" already defined
[ERROR]: Option "exclude_match" already defined
done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...[ERROR]: Option "quality" already defined
done
Initializing kdecompat options...[ERROR]: Option "plasma_thumbnails" already defined
[ERROR]: Option "present_windows" already defined
[ERROR]: Option "window_blur" already defined
[ERROR]: Option "sliding_popups" already defined
[ERROR]: Option "slide_in_duration" already defined
[ERROR]: Option "slide_out_duration" already defined
done
Initializing mag options...[ERROR]: Option "initiate" already defined
[ERROR]: Option "zoom_in_button" already defined
[ERROR]: Option "zoom_out_button" already defined
[ERROR]: Option "mode" already defined
[ERROR]: Option "zoom_factor" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "keep_screen" already defined
[ERROR]: Option "box_width" already defined
[ERROR]: Option "box_height" already defined
[ERROR]: Option "border" already defined
[ERROR]: Option "box_color" already defined
[ERROR]: Option "overlay" already defined
[ERROR]: Option "mask" already defined
[ERROR]: Option "x_offset" already defined
[ERROR]: Option "y_offset" already defined
[ERROR]: Option "radius" already defined
done
Initializing neg options...[ERROR]: Option "window_toggle_key" already defined
[ERROR]: Option "screen_toggle_key" already defined
[ERROR]: Option "neg_match" already defined
[ERROR]: Option "exclude_match" already defined
[ERROR]: Option "neg_decorations" already defined
done
Initializing obs options...done
Initializing opacify options...[ERROR]: Option "toggle_key" already defined
[ERROR]: Option "toggle_reset" already defined
[ERROR]: Option "timeout" already defined
[ERROR]: Option "init_toggle" already defined
[ERROR]: Option "only_if_block" already defined
[ERROR]: Option "focus_instant" already defined
[ERROR]: Option "no_delay_change" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "active_opacity" already defined
[ERROR]: Option "passive_opacity" already defined
done
Initializing opengl options...done
Initializing put options...[ERROR]: Option "put_viewport" already defined
[ERROR]: Option "put_viewport_1_key" already defined
[ERROR]: Option "put_viewport_2_key" already defined
[ERROR]: Option "put_viewport_3_key" already defined
[ERROR]: Option "put_viewport_4_key" already defined
[ERROR]: Option "put_viewport_5_key" already defined
[ERROR]: Option "put_viewport_6_key" already defined
[ERROR]: Option "put_viewport_7_key" already defined
[ERROR]: Option "put_viewport_8_key" already defined
[ERROR]: Option "put_viewport_9_key" already defined
[ERROR]: Option "put_viewport_10_key" already defined
[ERROR]: Option "put_viewport_11_key" already defined
[ERROR]: Option "put_viewport_12_key" already defined
[ERROR]: Option "put_viewport_left_key" already defined
[ERROR]: Option "put_viewport_right_key" already defined
[ERROR]: Option "put_viewport_up_key" already defined
[ERROR]: Option "put_viewport_down_key" already defined
[ERROR]: Option "put_center_key" already defined
[ERROR]: Option "put_center_button" already defined
[ERROR]: Option "put_left_key" already defined
[ERROR]: Option "put_left_button" already defined
[ERROR]: Option "put_right_key" already defined
[ERROR]: Option "put_right_button" already defined
[ERROR]: Option "put_top_key" already defined
[ERROR]: Option "put_top_button" already defined
[ERROR]: Option "put_bottom_key" already defined
[ERROR]: Option "put_bottom_button" already defined
[ERROR]: Option "put_topleft_key" already defined
[ERROR]: Option "put_topleft_button" already defined
[ERROR]: Option "put_topright_key" already defined
[ERROR]: Option "put_topright_button" already defined
[ERROR]: Option "put_bottomleft_key" already defined
[ERROR]: Option "put_bottomleft_button" already defined
[ERROR]: Option "put_bottomright_key" already defined
[ERROR]: Option "put_bottomright_button" already defined
[ERROR]: Option "put_empty_center_key" already defined
[ERROR]: Option "put_empty_center_button" already defined
[ERROR]: Option "put_empty_left_key" already defined
[ERROR]: Option "put_empty_left_button" already defined
[ERROR]: Option "put_empty_right_key" already defined
[ERROR]: Option "put_empty_right_button" already defined
[ERROR]: Option "put_empty_top_key" already defined
[ERROR]: Option "put_empty_top_button" already defined
[ERROR]: Option "put_empty_bottom_key" already defined
[ERROR]: Option "put_empty_bottom_button" already defined
[ERROR]: Option "put_empty_topleft_key" already defined
[ERROR]: Option "put_empty_topleft_button" already defined
[ERROR]: Option "put_empty_topright_key" already defined
[ERROR]: Option "put_empty_topright_button" already defined
[ERROR]: Option "put_empty_bottomleft_key" already defined
[ERROR]: Option "put_empty_bottomleft_button" already defined
[ERROR]: Option "put_empty_bottomright_key" already defined
[ERROR]: Option "put_empty_bottomright_button" already defined
[ERROR]: Option "put_restore_key" already defined
[ERROR]: Option "put_restore_button" already defined
[ERROR]: Option "put_pointer_key" already defined
[ERROR]: Option "put_pointer_button" already defined
[ERROR]: Option "put_next_output_key" already defined
[ERROR]: Option "put_next_output_button" already defined
[ERROR]: Option "put_put" already defined
[ERROR]: Option "pad_left" already defined
[ERROR]: Option "pad_right" already defined
[ERROR]: Option "pad_top" already defined
[ERROR]: Option "pad_bottom" already defined
[ERROR]: Option "unfocus_window" already defined
[ERROR]: Option "window_center" already defined
[ERROR]: Option "avoid_offscreen" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
done
Initializing resizeinfo options...[ERROR]: Option "fade_time" already defined
[ERROR]: Option "always_show" already defined
[ERROR]: Option "text_color" already defined
[ERROR]: Option "gradient_1" already defined
[ERROR]: Option "gradient_2" already defined
[ERROR]: Option "gradient_3" already defined
done
Initializing ring options...[ERROR]: Option "next_key" already defined
[ERROR]: Option "next_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "inactive_opacity" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "overlay_icon" already defined
[ERROR]: Option "darken_back" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "select_with_mouse" already defined
[ERROR]: Option "ring_clockwise" already defined
[ERROR]: Option "ring_width" already defined
[ERROR]: Option "ring_height" already defined
[ERROR]: Option "thumb_width" already defined
[ERROR]: Option "thumb_height" already defined
[ERROR]: Option "min_brightness" already defined
[ERROR]: Option "min_scale" already defined
[ERROR]: Option "window_title" already defined
[ERROR]: Option "title_font_bold" already defined
[ERROR]: Option "title_font_size" already defined
[ERROR]: Option "title_back_color" already defined
[ERROR]: Option "title_font_color" already defined
[ERROR]: Option "title_text_placement" already defined
done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...[ERROR]: Option "close_key" already defined
[ERROR]: Option "close_button" already defined
[ERROR]: Option "pull_key" already defined
[ERROR]: Option "pull_button" already defined
[ERROR]: Option "zoom_key" already defined
[ERROR]: Option "zoom_button" already defined
[ERROR]: Option "window_title" already defined
[ERROR]: Option "title_bold" already defined
[ERROR]: Option "title_size" already defined
[ERROR]: Option "border_size" already defined
[ERROR]: Option "font_color" already defined
[ERROR]: Option "back_color" already defined
[ERROR]: Option "window_highlight" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "layout_mode" already defined
[ERROR]: Option "natural_precision" already defined
[ERROR]: Option "constrain_pull_to_screen" already defined
[ERROR]: Option "exit_after_pull" already defined
done
Initializing screenshot options...done
Initializing shift options...[ERROR]: Option "initiate_key" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "initiate_edge" already defined
[ERROR]: Option "initiate_all_key" already defined
[ERROR]: Option "initiate_all_button" already defined
[ERROR]: Option "initiate_all_edge" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "next_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "shift_speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "mouse_speed" already defined
[ERROR]: Option "click_duration" already defined
[ERROR]: Option "mode" already defined
[ERROR]: Option "size" already defined
[ERROR]: Option "background_intensity" already defined
[ERROR]: Option "hide_all" already defined
[ERROR]: Option "reflection" already defined
[ERROR]: Option "ground_color1" already defined
[ERROR]: Option "ground_color2" already defined
[ERROR]: Option "ground_size" already defined
[ERROR]: Option "intensity" already defined
[ERROR]: Option "flip_rotation" already defined
[ERROR]: Option "cover_offset" already defined
[ERROR]: Option "cover_angle" already defined
[ERROR]: Option "cover_extra_space" already defined
[ERROR]: Option "cover_max_visible_windows" already defined
[ERROR]: Option "overlay_icon" already defined
[ERROR]: Option "mipmaps" already defined
[ERROR]: Option "multioutput_mode" already defined
[ERROR]: Option "window_title" already defined
[ERROR]: Option "title_font_bold" already defined
[ERROR]: Option "title_font_size" already defined
[ERROR]: Option "title_back_color" already defined
[ERROR]: Option "title_font_color" already defined
[ERROR]: Option "title_text_placement" already defined
done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...[ERROR]: Option "thumb_size" already defined
[ERROR]: Option "show_delay" already defined
[ERROR]: Option "border" already defined
[ERROR]: Option "thumb_color" already defined
[ERROR]: Option "fade_speed" already defined
[ERROR]: Option "current_viewport" already defined
[ERROR]: Option "always_on_top" already defined
[ERROR]: Option "window_like" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "title_enabled" already defined
[ERROR]: Option "font_bold" already defined
[ERROR]: Option "font_size" already defined
[ERROR]: Option "font_color" already defined
done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...[ERROR]: Option "skiptaskbar_match" already defined
[ERROR]: Option "skippager_match" already defined
[ERROR]: Option "above_match" already defined
[ERROR]: Option "below_match" already defined
[ERROR]: Option "sticky_match" already defined
[ERROR]: Option "fullscreen_match" already defined
[ERROR]: Option "maximize_match" already defined
[ERROR]: Option "no_argb_match" already defined
[ERROR]: Option "no_move_match" already defined
[ERROR]: Option "no_resize_match" already defined
[ERROR]: Option "no_minimize_match" already defined
[ERROR]: Option "no_maximize_match" already defined
[ERROR]: Option "no_close_match" already defined
[ERROR]: Option "no_focus_match" already defined
[ERROR]: Option "size_matches" already defined
[ERROR]: Option "size_width_values" already defined
[ERROR]: Option "size_height_values" already defined
done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00432

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00440
```

---

### Post by Tanker Bob on 2012-05-06
Sounds like you have an nVidia card. If so, please search the forums for the solution. In brief, you need to go to Ubuntu 2D, download the nVidia 295.49 drivers, do a Ctrl-Alt-F2, stop lightdm, then uninstall nvidia-current, nvidia-current-updates, nvidia-config, and nvidia-config-updates, then install the 295.49 drivers ignoring the warning about the pre-install script failing, then reboot.

---

### Post by slgtheindividual on 2012-05-06
> **Tanker Bob said:**
> Sounds like you have an nVidia card. If so, please search the forums for the solution. In brief, you need to go to Ubuntu 2D, download the nVidia 295.49 drivers, do a Ctrl-Alt-F2, stop lightdm, then uninstall nvidia-current, nvidia-current-updates, nvidia-config, and nvidia-config-updates, then install the 295.49 drivers ignoring the warning about the pre-install script failing, then reboot.


I don't I have an AMD ATI Radeon card.

---

### Post by Tanker Bob on 2012-05-06
There is a note about those on the kernel change logs [here](http://www.kernel.org/pub/linux/kernel/v3.x/ChangeLog-3.2.14). It was something about a bug in the 3.2 and 3.3 kernels that trips these drivers up.

---

### Post by slgtheindividual on 2012-05-07
> **Tanker Bob said:**
> There is a note about those on the kernel change logs [here]("http://www.kernel.org/pub/linux/kernel/v3.x/ChangeLog-3.2.14"). It was something about a bug in the 3.2 and 3.3 kernels that trips these drivers up.


thank you, I read that but I don't really know what it means, is there anything I can do about it?

---

### Post by Tanker Bob on 2012-05-07
> **slgtheindividual said:**
> thank you, I read that but I don't really know what it means, is there anything I can do about it?

I don't think so. The video driver developers need to work around the issue. Or, you could update your kernel to 3.4, which is not trivial.

Is there anything on the ATI Linux support forums about this? nVidia had a note from the developers on their forum within a few days as people reported the issues.

---

### Post by slgtheindividual on 2012-05-07
I fixed the problem but now for some reason I can only use unity 2d and if I boot into the standard ubuntu it just starts up in unity 2d.

Here's how I 'fixed' it

1st: ctrl + alt + t   to open a terminal
2nd: enter "jockey-gtk"
3rd: clicked ATI/AMD proprietary FGLRX graphics driver and then click activate

I then got an error message referring me to a log at /var/log/jockey.log

4th: clicked ATI/AMD proprietary FGLRX graphics driver (post release updates) and then click activate

I got the same error as previously

5th: again I clicked ATI/AMD proprietary FGLRX graphics driver and then click activate

this time it worked fine with no error and said I had to reboot for it to take affect

6th: alt + tab   to get back to the terminal then "sudo shutdown -h now" to shutdown

that was it, after reboot I'm getting a gui again, it's just unity 2d instead of 3d even on the default ubuntu profile, but it's better than nothing. 

If anybody has any advice for getting unity 3d back I'd be happy to try it out.

Thank you again to everyone who posted.

---

### Post by Tanker Bob on 2012-05-07
Wow, that was straightforward. Glad to hear that you at least have you system up an running, if less than optimally.

---

### Post by slgtheindividual on 2012-05-23
I got unity 3d to work now too,

I ran

/usr/lib/nux/unity_support_test -p

in the terminal and got all yes so I then ran

sudo nano environment

in /etc

and added the line 

UNITY_FORCE_START=1

logged out and logged back in and viola, unity 3d

---

