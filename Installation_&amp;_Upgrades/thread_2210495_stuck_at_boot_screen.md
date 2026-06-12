---
title: "stuck at boot screen"
date: 2014-03-11
forum: Installation &amp; Upgrades
---

### Post by xiqual34 on 2014-03-11
new laptop, msi, 4th generation intel chip
ubuntu 13.10 installed.
i was able to login, work normally.
after a couple of days I got a message 'loading initial ramdisk' on boot screen.
reading through the forums, i added to grub cmd:

i915.i915_enable_rc6=1, acpi_osi=Linux (without comma, can't remember which order)

and it worked.

then after a couple of days, i was not able to login again.
so i tried different options from [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power)
and it worked again.

two days later, i am again not able to login to ubuntu.

previously i had tried to install nvidia drivers (because i have nvidia geforce card). this caused a catastrophe, i had to reinstall ubuntu.

does anyone have ideas on how to solve this problem?

also more importantly **why** is it happening? why would the options above work, only to fail after a couple of days?
laptop model is msi gs70.

note: i have also tried acpi=0, acpi_backlight=vendor, i915.modeset=0, nouveau.modeset=0, nomodeset, video=1280x1024-24@60, video=1:1280x1024-24@60, none of these options worked.

any help/comments would be appreciated.

---

### Post by xiqual34 on 2014-03-11
how do you boot in text mode? by replacing quiet splash with text?
if so, that doesn't work.
i'd just like to get some feedback from the system to see why it gets stuck. blank screen/loading initial ramdisk is very frustrating...

---

### Post by xiqual34 on 2014-03-12
update:
after doing some research, found out that by adding plymouth:debug to the grub options, ubuntu proceeds to boot.
This is my plymouth log. Can anyone please tell me if they spot anything wrong?

Not sure whether I should mark the thread as solved. Hopefully tomorrow or the day after I will no longer have these problems.

```
[main.c]                                 check_logging:checking if console messages should be redirected and logged 
[main.c]                                 check_logging:logging will be enabled! 
[main.c]                        initialize_environment:source built on Aug  1 2013 
[main.c]                        initialize_environment:checking if '/dev/tty7' exists 
[main.c]                            check_for_consoles:checking for consoles 
[main.c]                        add_consoles_from_file:opening /sys/class/tty/console/active 
[main.c]                        add_consoles_from_file:reading file 
[main.c]                        add_consoles_from_file:console /dev/tty0 found! 
[main.c]                            check_for_consoles:After processing serial consoles there are now 0 text displays 
[main.c]                redirect_standard_io_to_device:redirecting stdio to /dev/tty7 
[main.c]                        initialize_environment:Making sure /run/plymouth exists 
[main.c]                        initialize_environment:initialized minimal work environment 
[main.c]                     attach_to_running_session:creating new terminal session 
[ply-terminal-session.c]                   ply_terminal_session_attach:ptmx not passed in, creating one 
[ply-terminal-session.c]                           open_pseudoterminal:opening device '/dev/ptmx' 
[ply-terminal-session.c]                           open_pseudoterminal: opened device '/dev/ptmx' 
[ply-terminal-session.c]                           open_pseudoterminal:creating pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:done creating pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:unlocking pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:unlocked pseudoterminal 
[ply-terminal-session.c]                   ply_terminal_session_attach:redirecting system console to terminal device 
[ply-terminal-session.c]                   ply_terminal_session_attach:done redirecting system console to terminal device 
[ply-terminal-session.c]            ply_terminal_session_start_logging:logging incoming console messages 
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration' 
[main.c]                                          main:entering event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 603 (/bin/plymouth show-splash) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got show splash request 
[main.c]      plymouth_should_ignore_show_splash_calls:checking if plymouth should be running 
[main.c]                            check_for_consoles:checking for consoles and adding displays 
[main.c]                        add_consoles_from_file:opening /sys/class/tty/console/active 
[main.c]                        add_consoles_from_file:reading file 
[main.c]                        add_consoles_from_file:console /dev/tty0 found! 
[main.c]             add_default_displays_and_keyboard:adding default displays and keyboard 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/x86_64-linux-gnu/plymouth/renderers/x11.so 
[ply-utils.c]                               ply_open_module:Could not load module "/lib/x86_64-linux-gnu/plymouth/renderers/x11.so": /lib/x86_64-linux-gnu/plymouth/renderers/x11.so: cannot open shared object file: No such file or directory
 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/x86_64-linux-gnu/plymouth/renderers/drm.so 
[./plugin.c]                                create_backend:creating renderer backend for device /dev/dri/card0 
[./plugin.c]                                   load_driver:Attempting to load driver 'i915' 
[ply-terminal.c]                             ply_terminal_open:trying to open terminal '/dev/tty7' 
[ply-terminal.c]                 ply_terminal_look_up_geometry:looking up terminal text geometry 
[ply-terminal.c]                 ply_terminal_look_up_geometry:terminal is now 240x67 text cells 
[ply-terminal.c]                                 get_active_vt:Remembering that initial vt is 1 
[./plugin.c]                   find_controller_for_encoder:Found already lit monitor 
[./plugin.c]                      get_index_of_active_mode:Looking for connector mode index of active mode 1920x1080 
[./plugin.c]                            find_index_of_mode:Found connector mode index 0 for mode 1920x1080 
[./plugin.c]               ply_renderer_head_add_connector:Adding connector with id 12 to 1920x1080 head 
[./plugin.c]                         ply_renderer_head_new:Creating 1920x1080 renderer head 
[./ply-renderer-generic-driver.c]                       ply_renderer_buffer_new:returning 1x1 buffer with stride 64 
[ply-renderer.c]                      ply_renderer_open_plugin:opened renderer plugin /lib/x86_64-linux-gnu/plymouth/renderers/drm.so 
[main.c]                                  set_keyboard:listening for keystrokes 
[main.c]                                  set_keyboard:listening for backspace 
[main.c]                                  set_keyboard:listening for enter 
[main.c]              add_pixel_displays_from_renderer:Adding displays for 1 heads 
[main.c]                            check_for_consoles:After processing serial consoles there are now 1 text displays 
[main.c]                            check_for_consoles:bootloader handed off on VT7. 
[main.c]           plymouth_should_show_default_splash:checking if plymouth should show default splash 
[main.c]           plymouth_should_show_default_splash:using default splash because kernel command line has option "splash" 
[main.c]                           show_default_splash:Showing splash screen 
[main.c]                    find_system_default_splash:Trying to load /etc/plymouth//plymouthd.conf 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory 
[main.c]                    find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf 
[main.c]              find_distribution_default_splash:Trying to load /lib/plymouth//plymouthd.defaults 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth//plymouthd.defaults: No such file or directory 
[main.c]              find_distribution_default_splash:failed to load /lib/plymouth//plymouthd.defaults 
[main.c]                           show_default_splash:Trying old scheme for default splash 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/default.plymouth' 
[ply-key-file.c]                       ply_key_file_load_group:trying to load group Plymouth Theme 
[ply-key-file.c]                       ply_key_file_load_group:trying to load group script 
[ply-key-file.c]                      ply_key_file_load_groups:key file has no more groups 
[main.c]                             start_boot_splash:attaching plugin to event loop 
[main.c]                             start_boot_splash:attaching progress to plugin 
[main.c]      add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash 
[main.c]      add_displays_and_keyboard_to_boot_splash:adding pixel display on boot splash 
[main.c]      add_displays_and_keyboard_to_boot_splash:adding text display on boot splash 
[main.c]                             start_boot_splash:showing plugin 
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen 
[./plugin.c]                            show_splash_screen:starting boot animation 
[./plugin.c]                               start_animation:parsing script file 
[./plugin.c]                        start_script_animation:executing script file 
[ply-label.c]                                ply_label_free:Unloading label control plugin 
[ply-label.c]                                ply_label_free:Unloading label control plugin 
[ply-label.c]                                ply_label_free:Unloading label control plugin 
[ply-label.c]                                ply_label_free:Unloading label control plugin 
[./plugin.c]                         ply_renderer_head_map:Creating buffer for 1920x1080 renderer head 
[./ply-renderer-generic-driver.c]                       ply_renderer_buffer_new:returning 1920x1080 buffer with stride 7680 
[./plugin.c]                         ply_renderer_head_map:Mapping buffer for 1920x1080 renderer head 
[./plugin.c]                      ply_renderer_head_redraw:Redrawing 1920x1080 renderer head 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[./plugin.c]                          on_active_vt_changed:activating on vt change 
[./plugin.c]                                      activate:taking master and scanning out 
[./plugin.c]         ply_renderer_head_set_scan_out_buffer:Setting scan out buffer of 1920x1080 head to our buffer 
[./plugin.c]                                    flush_head:Needed to reset scan out buffer on 1920x1080 renderer head 
[./plugin.c]         ply_renderer_head_set_scan_out_buffer:Setting scan out buffer of 1920x1080 head to our buffer 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 9 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 9 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 9 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 9 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 9 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 9 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 9 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 680 (/bin/plymouth update-root-fs --read-write) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got system initialized notification 
[main.c]                         on_system_initialized:system now initialized, opening log 
[main.c]                         get_log_file_for_mode:returning log file '/var/log/boot.log' 
[main.c]                               prepare_logging:opening log '/var/log/boot.log' 
[ply-utils.c]                  ply_get_process_command_line:Could not open /proc/693/cmdline: No such file or directory 
[ply-utils.c]                    ply_get_process_parent_pid:Could not open /proc/693/stat: No such file or directory 
[ply-utils.c]                  ply_get_process_command_line:Could not open /proc/0/cmdline: No such file or directory 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 693 ((null)) with parent pid 0 ((null)) 
[ply-boot-server.c]                ply_boot_connection_on_request:could not finish writing ack: Broken pipe 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 12 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 12 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 12 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 12 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 12 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 12 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 12 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'systemd-logind' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'bluetooth' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 753 (plymouth --ping) with parent pid 717 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'avahi-daemon' 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 14 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 14 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 14 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 14 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 14 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 14 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 14 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'avahi-cups-reload' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'avahi-cups-reload' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-manager' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'cups' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'cups-browsed' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'plymouth-splash' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'plymouth-log' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 883 (plymouth --ping) with parent pid 717 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 889 (plymouth --ping) with parent pid 717 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 907 (plymouth --ping) with parent pid 900 (/bin/sh /etc/rcS.d/S70x11-common start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 912 (plymouth --ping) with parent pid 900 (/bin/sh /etc/rcS.d/S70x11-common start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 918 (plymouth --ping) with parent pid 900 (/bin/sh /etc/rcS.d/S70x11-common start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'rc-sysinit' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'rc' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty4' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty5' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'alsa-restore' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'acpid' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty2' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty3' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'dmesg' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty6' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'hybrid-gfx' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'plymouth-stop' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-interface-security' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'apport' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'irqbalance' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'alsa-state' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'hybrid-gfx' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'networking' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1049 (plymouth --ping) with parent pid 1030 (lightdm) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1051 (plymouth --has-active-vt) with parent pid 1030 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got has_active vt? request 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1052 (plymouth deactivate) with parent pid 1030 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got deactivate request 
[main.c]                                 on_deactivate:deactivating 
[main.c]                                 on_deactivate:deactivating keyboard 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 11 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 11 
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle 
[ply-boot-splash.c]                                       on_idle:splash now idle 
[main.c]                           on_boot_splash_idle:boot splash idle 
[main.c]                           on_boot_splash_idle:deactivating splash 
[main.c]                             deactivate_splash:deactivating renderer 
[./plugin.c]                                    deactivate:dropping master 
[main.c]                   detach_from_running_session:detaching from terminal session 
[ply-terminal-session.c]                   ply_terminal_session_detach:stopping terminal logger 
[ply-terminal-session.c]             ply_terminal_session_stop_logging:stopping logging of incoming console messages 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 8 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 8 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 8, removing source 
[ply-terminal-session.c]                   ply_terminal_session_detach:unredirecting console messages 
[ply-terminal-session.c]                   ply_terminal_session_detach:ptmx wasn't originally passed in, destroying created one 
[main.c]                             deactivate_splash:deactivating terminal 
[ply-boot-server.c]            ply_boot_connection_on_deactivated:deactivated 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1079 (plymouth --ping) with parent pid 1071 (/bin/sh /etc/rc2.d/S70dns-clean start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1084 (plymouth --ping) with parent pid 1071 (/bin/sh /etc/rc2.d/S70dns-clean start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1090 (plymouth --ping) with parent pid 1071 (/bin/sh /etc/rc2.d/S70dns-clean start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'cron' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'alsa-restore' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'ureadahead' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1141 (plymouth --ping) with parent pid 1130 (/bin/sh /etc/rc2.d/S91apache2 start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405b60 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405fb0, 0x405b60) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'dmesg' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'whoopsie' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'startpar-bridge' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'udevtrigger' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'udevmonitor' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'udev-finish' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'udev-finish' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'rc' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty1' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 731 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'mysql' 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1337 (plymouth quit --retain-splash) with parent pid 1030 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got quit --retain-splash request 
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration' 
[main.c]                                       on_quit:time to quit, closing log 
[main.c]                                       on_quit:deactivating keyboard 
[main.c]                                       on_quit:unloading splash 
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle 
[ply-boot-splash.c]                                       on_idle:splash now idle 
[main.c]                           on_boot_splash_idle:boot splash idle 
[main.c]                           on_boot_splash_idle:quitting splash 
[main.c]                                   quit_splash:quiting splash 
[main.c]                                   quit_splash:freeing splash 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[ply-event-loop.c]      ply_event_loop_stop_watching_for_timeout:multiple matching timeouts found for removal 
[ply-event-loop.c]      ply_event_loop_stop_watching_for_timeout:multiple matching timeouts found for removal 
[ply-boot-splash.c]                               remove_displays:removing pixel displays 
[ply-boot-splash.c]                               remove_displays:Removing 1920x1080 pixel display 
[ply-boot-splash.c]                               remove_displays:Removing node 
[ply-boot-splash.c]                               remove_displays:removing text displays 
[ply-boot-splash.c]                               remove_displays:Removing 240x67 text display 
[ply-boot-splash.c]                               remove_displays:Removing node 
[main.c]                                   quit_splash:removing displays and keyboard 
[main.c]                  remove_displays_and_keyboard:removing displays and keyboard 
[main.c]                  remove_displays_and_keyboard:removing pixel display 
[main.c]                  remove_displays_and_keyboard:removing text display 
[main.c]                  remove_displays_and_keyboard:removing keyboard 
[./plugin.c]                       ply_renderer_head_unmap:unmapping 1920x1080 renderer head 
[./plugin.c]                                  close_device:closing device 
[./plugin.c]                        ply_renderer_head_free:freeing 1920x1080 renderer head 
[./plugin.c]                                 unload_driver:unloading driver 
[ply-renderer.c]                             ply_renderer_free:Unloading renderer backend plugin 
[ply-terminal.c]                            ply_terminal_close:restoring color palette 
[ply-terminal.c]                            ply_terminal_close:stop watching tty fd 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 11 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 11 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 11, removing source 
[ply-terminal.c]                            ply_terminal_close:stop watching SIGWINCH signal 
[ply-terminal.c]                            ply_terminal_close:setting buffered input 
[main.c]                           on_boot_splash_idle:quitting program 
[main.c]                                  quit_program:exiting event loop 
[ply-boot-server.c]          ply_boot_connection_on_quit_complete:quit complete 
[main.c]                                          main:exited event loop 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[main.c]                                          main:freeing terminal session 
[ply-terminal-session.c]             ply_terminal_session_stop_logging:stopping logging of incoming console messages 
[main.c]                                          main:exiting with code 0
```

---

