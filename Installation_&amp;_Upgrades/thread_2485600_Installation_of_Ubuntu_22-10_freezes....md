---
title: "Installation of Ubuntu 22-10 freezes..."
date: 2023-04-03
forum: Installation &amp; Upgrades
---

### Post by dmk-4u on 2023-04-03
Hi, I am new to this forum.

I haven´t got much experience with linux, but basically I installed the OS a couple of times successfully. But not this time ant that is really getting me.

Now to the hardware..

It is an ASUS X550VX (with BIOS updated today to the latest version) with a rather old drive, which I threw out for a new SAMSUNG 1TB SSD. First I tried to install the LTD - Version but that failed already.

Then I moved to the latest version 22.10 but that happened again. So I "googled" to add the "nomodeset" line, but that didn´t do it as well.
Then I tried to add another rater squiky command: "GRUB_CMDLINE_LINUX="i915.enable_guc=0"

Still no effect... If I hurry up, I come to the 5-th page, then it stalls. If I do nothing it stalles right away... 

Is there anything else I could try? (Besides I tried already 2 different USB-Sticks. Bios is updated, and "fast Boot" and "secure Boot" disabled. 

Now I put Windows on it to have a second choice and this went ok with the usb-stick in no time.. I left about 480 GB of space for UBUNTU if I ever get it to work... ;O)

I created the USB with Rufus and GPT

Greetings


Daniel

---

### Post by ajgreeny on 2023-04-03
It would help us a lot more if you tell us in much more detail what the hardware is.
If necessary you can do this using a live version of Ubuntu running from the USB by opening up a terminal and running command ```
inxi -Fzx
```(you may need to install **inxi** first but try it and you will be told if it's already installed or  not.

Copy that terminal output with the mouse using right click on the highlighted text and then paste it back here in your reply using [Code-Tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168")

---

### Post by dmk-4u on 2023-04-04
Hi ajgreeny,

thank you for the post! I tried to start "Try Ubuntu" but still it freezes. I will post the screen (Foto). Maybe this helps already a bit...

Greetings 


Daniel

---

### Post by tea for one on 2023-04-04
> **dmk-4u said:**
> Is there anything else I could try? (Besides I tried already 2 different USB-Sticks. Bios is updated, and "fast Boot" and "secure Boot" disabled.
Double-check/disable the following UEFI settings (if they exist on your PC):-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)

Your screenshot in post 3 showed a TPM comment.

---

### Post by dmk-4u on 2023-04-05
Hi, yes I doublechecked and I thought I did prepare, what I could prepare...

BUT, the TPM isn´t to be found in this Bios and this brought me to the point where I googled a bit in the internet. No I learned that with this kind of asus laptops the TPM can´t be swiched off. What a bummer!

If you know a workaround then great! If not at least I now know that it isn ´t feesible...

Greetings!

---

### Post by tea for one on 2023-04-05
> **dmk-4u said:**
> If you know a workaround then great! 
Unfortunately, I do not know an instant workaround - just educated guesses at the moment.
However, I would disable Intel AES-NI in image 5 (some sort of encryption possibly?)

I'm wondering if there may be other Security/Advanced UEFI options which may prevent an Ubuntu installation.
There is a lack of consistency in every vendor's UEFI firmware and, more often than not, trial and error is the only way forward.

---

### Post by tea for one on 2023-04-05
Can you find a UEFI setting "Trust Platform Technology"?

Another Asus user had a similar problem.
[https://unix.stackexchange.com/questions/422454/acpi-region-does-not-cover-the-entire-command-response-buffer](https://unix.stackexchange.com/questions/422454/acpi-region-does-not-cover-the-entire-command-response-buffer)

---

### Post by MAFoElffen on 2023-04-06
I have an idea to get the information we need to be able to come up with informed recommendations...

While booting the LiveUSB media, it is going to display the Grub2 boot menu. (These instructions assume you have a wired internet connection)

At that menu, press the <E> key. <Arrow-Down> until the cursor gets to the line that starts with "linux"...

At that line <Arrow-Right> until you get to where it says "quiet splash". replace "quite splash" with "--- 3" (3 dashes, then numeric 3). Press <Cntrl><X> to boot.

- Does it display the boot messages during the boot process?
- Did you notice any error message in those messages?
- Does it boot to a command line?

This should boot to a command line, run level 3, without graphics. At the command line, do this:
```

sudo apt-add-respository ppa:mafoelffen/system-info

```
Press <Enter> to confirm... Then 
```

sudo apt update
sudo apt install -y system-info
system-info

```
When it asks you if you want to upload the report to a pastebin, answer <y><Enter>

Copy down the URL to post here.

---

### Post by ActionParsnip on 2023-04-07
Is this a dual boot or is Ubuntu the only OS on the system?

---

### Post by dmk-4u on 2023-04-07
Great, I´ll try that in 2 days as I´m off to another country to see famly but I´m taking the laptop with me and If I have a quiet second I´ll try this.. and give you feedback...

---

### Post by dmk-4u on 2023-04-07
@ActionParsnip

At first I wanted it to be a single boot only option. But I tried the win installation in order to find out if it would be a hardware-based problem, but it worked out allright. So at the moment in order to be able to work I´ll leave it as it is. Later I will see (I left an empty partition big enough to be able to install Ubuntu and have fun)... ;O)

Greetings...

---

### Post by kinddolphin8827 on 2023-04-13
It seems to me like you may have a glitch in the  open source NVIDIA driver. Might I suggest that you try to log onto the effected machine? 

Have you tried maybe downloading the live CD version of Debian or another distribution as a way to extract the log information?

Have you considered purchasing a whole other  SSD or HDD and then doing a fresh installation of 22.04?

---

