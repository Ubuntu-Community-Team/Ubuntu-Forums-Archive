---
title: "Lucid vdpau ppa + 195.36.08 nvidia driver not working !"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jackallen0714 on 2010-03-08
I added vdpau ppa to the software resource and installed the nvidia-current driver 

After an upgrade near alpha 3, mplayer stops working when I choose vdpau as video output, and I find some error in log:

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

Then I installed vdpauinfo and found

$ vdpauinfo 
display: :0.0   screen: 0
Error creating VDPAU device: 1

Any idea or solution ?:o

---

### Post by biasquez on 2010-03-08
> **jackallen0714 said:**
> I added vdpau ppa to the software resource and installed the nvidia-current driver 

After an upgrade near alpha 3, mplayer stops working when I choose vdpau as video output, and I find some error in log:

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

Then I installed vdpauinfo and found

$ vdpauinfo 
display: :0.0   screen: 0
Error creating VDPAU device: 1

Any idea or solution ?:o

i have same problem

---

### Post by Technoviking on 2010-03-08
Is the vdpau ppa even needed? I install nvidia-current and mplayer from the Lucid repos and the vdpau driver shows up in mplayer and works fine for me.

T-V

---

### Post by biasquez on 2010-03-08
> **Technoviking said:**
> Is the vdpau ppa even needed? I install nvidia-current and mplayer from the Lucid repos and the vdpau driver shows up in mplayer and works fine for me.

T-V

i installed nvidia-current and mplayer from lucid repos but vdpau driver doesn't work.

---

### Post by zekopeko on 2010-03-08
All I'm getting with smplayer are pink/red artifacts for picture.

---

