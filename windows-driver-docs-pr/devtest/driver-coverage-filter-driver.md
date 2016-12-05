---
title: Driver Coverage Filter Driver
description: Driver Coverage Filter Driver
ms.assetid: 8d345081-b9be-4e22-9276-dacd7815f506
keywords: ["Driver Coverage Toolkit WDK , filter driver"]
---

# Driver Coverage Filter Driver


**Note**  The Driver Coverage Toolkit is no longer needed in Windows 10 and the installer is no longer included in the WDK. To perform tasks described here in Windows 10, instead use [Driver Verifier](driver-verifier.md) and [IRP Logging](irp-logging.md).

 

The Driver Coverage filter driver (Drvcov.sys) monitors the I/O request packets (IRPs) that enter or leave the driver stack of specified devices. You specify the devices that the Driver Coverage filter driver monitors by using the *DQ* parameter when you run the **Enable IRP Coverage data collection** tool. See [How to select and configure the Device Fundamentals tests](https://msdn.microsoft.com/windows-drivers/develop/how_to_select_and_configure_the_device_fundamental_tests) and [Device Fundamentals Test Parameters](https://msdn.microsoft.com/windows-drivers/develop/how_to_select_and_configure_the_device_fundamental_tests).

<span id="UpperFilter___TRUE"></span><span id="upperfilter___true"></span><span id="UPPERFILTER___TRUE"></span>**UpperFilter = TRUE**  
This option installs the Driver Coverage filter driver as an upper filter to the device driver for the specified device. This configuration monitors all IRP traffic into or out of the device driver within the device's driver stack, regardless of whether the driver processed the IRP or passed it through to lower device drivers.

<span id="UpperFilter___FALSE"></span><span id="upperfilter___false"></span><span id="UPPERFILTER___FALSE"></span>**UpperFilter = FALSE**  
This option installs the Driver Coverage filter driver as a lower filter to the device driver for the specified device. This configuration monitors all IRP traffic into or out of the device driver from lower drivers within the device's driver stack.

The following figure shows a driver stack and IRP monitoring window for a device where the Driver Coverage filter driver is installed as an upper filter. In this configuration, the filter driver tracks all IRPs that enter or leave the driver for the specified device.

![diagram illustrating a driver coverage filter driver installed as an upper filter](images/coverage-1.png)

The following figure shows a driver stack and IRP monitoring window for a device where the Driver Coverage filter driver is installed as a lower filter. In this configuration, the filter driver tracks all IRPs that enter or leave the device driver for the specified device's driver stack.

![diagram illustrating a driver coverage filter driver installed as a lower filter](images/coverage-2.png)

.

### <span id="installing_the_driver_coverage_filter_driver"></span><span id="INSTALLING_THE_DRIVER_COVERAGE_FILTER_DRIVER"></span> Installing the Driver Coverage filter driver

The following rules define the best way to install the Driver Coverage filter driver to monitor IRPs:

-   If you want coverage data for IRP traffic between a specific device and user-mode applications or services, install the filter driver as an upper filter to the driver for the device.

-   If you want coverage data for IRP traffic between the specified device and devices lower in the driver stack, such as the bus driver for the device, install the filter driver as a lower filter to the driver for the device.

**Note**   How you install the Driver Coverage filter driver for optimal IRP coverage depends on the topology of the driver stack and requires that you understand the relationship and order of the drivers within the stack.

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[devtest\devtest]:%20Driver%20Coverage%20Filter%20Driver%20%20RELEASE:%20%2811/17/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



