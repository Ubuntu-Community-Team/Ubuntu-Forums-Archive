---
title: "Ubuntu18.04 downgrade to 430.50 problem (Docker gpu)"
date: 2020-01-04
forum: Installation &amp; Upgrades
---

### Post by goupil35000 on 2020-01-04
Hi,
I have a problem with Docker GPU. It seems that my applications are not working with 435 and 440 drivers, but it was working with 430.50. Unfortunately, driver 430 is no longer present in "Software and Updates" and trying to install it with apt-get installs only driver 440 (even if I choose 415 in "Software and Updates" and Apply, it doesn't work and is going back to 440 driver). And 430 driver is not in the list now.
How to force installation of driver 430.50 ? One important thing is I need to also have dkms because I have some special devices which need compilation.
Thanks for reply


Goupil


For information, the problem is (docker-ce 19.03):
>> docker run --gpus all --rm nvidia/cuda nvidia-smi
docker: Error response from daemon: OCI runtime create failed: container_linux.go:346: starting container process caused "process_linux.go:449: container init caused \"process_linux.go:432: running prestart hook 0 caused \\\"error running hook: exit status 1, stdout: , stderr: nvidia-container-cli: detection error: driver error: failed to process request\\\\n\\\"\"": unknown.

---

### Post by CatKiller on 2020-01-04
I know nothing about Docker GPU, but as a general rule you can't cleanly change between branches of the nvidia driver. You need to purge everything from the old branch and then install the new branch, otherwise it doesn't work. The graphics driver PPA has the 430 branch, if you were using that. Otherwise, you'll need to say what you are using.

---

### Post by goupil35000 on 2020-01-05
Hello CatKiller,

Thanks for your answer.

I purge everything. But my problem is even if i try to install with "sudo apt-get install nvidia-driver-430", all the messages are about 440 and it appears in application "Nvidia X server settings" as 440.

Goupil

---

