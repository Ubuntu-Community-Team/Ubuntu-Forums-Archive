---
title: "Can Not Install On MacBook Pro"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by kennyboy7 on 2010-07-19
I am at my wits end with this. I am trying to install Ubuntu 10.04 on my MacBook Pro using Virtual Box. I have tried different downloads and copied them to CD's and DVD's. I have tried installing directly from the ISO file as well. I have also tried directly booting the CD or DVD using the "C" option on boot up. It will just not go into the install mode. The closest I get will be just a black screen with the "Shell" prompt. Can anybody give me some ideas as to what I am doing wrong? Any ideas and help would be appreciated.

Ken

---

### Post by JustinR on 2010-07-19
Set the Ubuntu 10.04 ISO as the CD Rom for your Virtual Machine and make sure CD Rom is the first bootup option.

---

### Post by kennyboy7 on 2010-07-20
Thanks for your reply Justin. But that still didn't work. i still get a black screen that says EFI Shell version 2.10 [1.1] and then a shell prompt. I hope you or someone else has some ideas.

Ken

---

### Post by JustinR on 2010-07-20
Okay can you post the .xml file from your Virtual Machine? Its usually in the Machines folder and then in the Virtual Machines Name's folder.

---

### Post by kennyboy7 on 2010-07-20
Thanks again for your help Justin. I think this is what you are looking for.

Ken



<?xml version="1.0"?>
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.10-macosx">
  <Machine uuid="{72506531-3b7b-40bf-a566-59dcec9e9670}" name="Ubuntu Linux" OSType="Ubuntu" lastStateChange="2010-07-20T05:27:28Z">
    <ExtraData>
      <ExtraDataItem name="GUI/LastCloseAction" value="powerOff"/>
      <ExtraDataItem name="GUI/LastGuestSizeHint" value="1024,768"/>
      <ExtraDataItem name="GUI/LastWindowPostion" value="823,249,1024,790"/>
      <ExtraDataItem name="GUI/MiniToolBarAlignment" value="bottom"/>
      <ExtraDataItem name="GUI/SaveMountedAtRuntime" value="yes"/>
      <ExtraDataItem name="GUI/ShowMiniToolBar" value="yes"/>
    </ExtraData>
    <Hardware version="2">
      <CPU count="1" hotplug="false">
        <HardwareVirtEx enabled="true" exclusive="false"/>
        <HardwareVirtExNestedPaging enabled="true"/>
        <HardwareVirtExVPID enabled="true"/>
        <PAE enabled="true"/>
      </CPU>
      <Memory RAMSize="512" PageFusion="false"/>
      <Firmware type="EFI"/>
      <HID Pointing="USBTablet" Keyboard="PS2Keyboard"/>
      <HPET enabled="false"/>
      <Boot>
        <Order position="1" device="DVD"/>
        <Order position="2" device="HardDisk"/>
        <Order position="3" device="None"/>
        <Order position="4" device="None"/>
      </Boot>
      <Display VRAMSize="12" monitorCount="1" accelerate3D="false" accelerate2DVideo="false"/>
      <RemoteDisplay enabled="false" port="3389" authType="Null" authTimeout="5000">
        <VideoChannel enabled="false" quality="75"/>
      </RemoteDisplay>
      <BIOS>
        <ACPI enabled="true"/>
        <IOAPIC enabled="false"/>
        <Logo fadeIn="true" fadeOut="true" displayTime="0"/>
        <BootMenu mode="MessageAndMenu"/>
        <TimeOffset value="0"/>
        <PXEDebug enabled="false"/>
      </BIOS>
      <USBController enabled="true" enabledEhci="true"/>
      <Network>
        <Adapter slot="0" enabled="true" MACAddress="0800271ED339" cable="true" speed="0" type="82540EM">
          <NAT>
            <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
            <Alias logging="false" proxy-only="false" use-same-ports="false"/>
          </NAT>
        </Adapter>
        <Adapter slot="1" enabled="false" MACAddress="0800278F1F17" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="2" enabled="false" MACAddress="0800272998B5" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="3" enabled="false" MACAddress="080027BA1EBB" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="4" enabled="false" MACAddress="080027DC1720" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="5" enabled="false" MACAddress="080027EB0381" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="6" enabled="false" MACAddress="0800275F609C" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
        <Adapter slot="7" enabled="false" MACAddress="080027CB4CBC" cable="true" speed="0" type="82540EM">
          <DisabledModes>
            <NAT>
              <DNS pass-domain="true" use-proxy="false" use-host-resolver="false"/>
              <Alias logging="false" proxy-only="false" use-same-ports="false"/>
            </NAT>
          </DisabledModes>
        </Adapter>
      </Network>
      <UART>
        <Port slot="0" enabled="false" IOBase="0x3f8" IRQ="4" hostMode="Disconnected"/>
        <Port slot="1" enabled="false" IOBase="0x3f8" IRQ="4" hostMode="Disconnected"/>
      </UART>
      <LPT>
        <Port slot="0" enabled="false" IOBase="0x378" IRQ="4"/>
        <Port slot="1" enabled="false" IOBase="0x378" IRQ="4"/>
      </LPT>
      <AudioAdapter controller="AC97" driver="CoreAudio" enabled="true"/>
      <RTC localOrUTC="UTC"/>
      <SharedFolders/>
      <Clipboard mode="Bidirectional"/>
      <IO>
        <IoCache enabled="true" size="5"/>
        <IoBandwidth max="0"/>
      </IO>
      <Guest memoryBalloonSize="0"/>
      <GuestProperties>
        <GuestProperty name="/VirtualBox/HostInfo/GUI/LanguageID" value="en_US" timestamp="1279603474208223000" flags=""/>
      </GuestProperties>
    </Hardware>
    <StorageControllers>
      <StorageController name="IDE Controller" type="PIIX4" PortCount="2" useHostIOCache="true">
        <AttachedDevice passthrough="false" type="DVD" port="1" device="0"/>
      </StorageController>
      <StorageController name="SATA Controller" type="AHCI" PortCount="1" useHostIOCache="false" IDE0MasterEmulationPort="0" IDE0SlaveEmulationPort="1" IDE1MasterEmulationPort="2" IDE1SlaveEmulationPort="3">
        <AttachedDevice type="HardDisk" port="0" device="0">
          <Image uuid="{f2ed7960-8dcc-495c-9250-986e754807c9}"/>
        </AttachedDevice>
      </StorageController>
    </StorageControllers>
  </Machine>
</VirtualBox>

---

### Post by JustinR on 2010-07-20
Hi it appears that EFI is enabled - which isn't required for Ubuntu. Under the Systems Tab in your Virtual Machine's settings uncheck the box that says 'Enable EFI (special OS's only)' and see if your Virtual Machine starts.

---

### Post by kennyboy7 on 2010-07-21
Thanks again Justin


I think that did it. I am getting the install screen now and using just the image and not a CD. I will let you know how it goes. Thanks so much again.

Ken

---

### Post by JustinR on 2010-07-21
Your welcome! If you disabled EFI then the CD should now start working fine. Good luck!

---

