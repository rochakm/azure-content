<properties 
	pageTitle="How to Manage Streaming Endpoints in a Media Services Account" 
	description="This topic shows how to manage Streaming Endpoints using the Azure Management Portal." 
	services="media-services" 
	documentationCenter="" 
	authors="juliako" 
	writer="juliako" 
	manager="dwrede" 
	editor=""/>

<tags 
	ms.service="media-services" 
	ms.workload="media" 
	ms.tgt_pltfrm="na" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="02/15/2015" 
	ms.author="juliako"/>


#<a id="managemediaservicesorigins"></a>How to Manage Streaming Endpoints in a Media Services Account

This article is part of the [Media Services Video on Demand workflow](../media-services-video-on-demand-workflow) and [Media Services Live Streaming workflow](../media-services-live-streaming-workflow) series.  


In Media Services, a Streaming Endpoint represents a streaming service that can deliver content directly to a client player application, or to a Content Delivery Network (CDN) for further distribution. Currently, Microsoft Azure Media Services does not offer a seamless CDN integration, but you can utilize one of the CDN providers on the market (Azure CDN or Akamai). The outbound stream from the Streaming Endpoint service can be a live stream, or a video on demand Asset in your Media Services account. 

In addition, you can control the capacity of the Streaming Endpoint service to handle growing bandwidth needs by adjusting scale units (also known as streaming units). It is recommended to allocate one or more scale units for applications in production environment. Scale units provide you with both dedicated egress capacity that can be purchased in increments of 200 Mbps and additional functionality which currently includes use dynamic packaging. 

This topic shows how to manage Streaming Endpoints using the Azure Management Portal.


##Adding and Deleting Streaming Endpoints 

1. In the [Management Portal](https://manage.windowsazure.com/), click **Media Services**. Then, click the name of the media service.
2. Select the **STREAMING ENDPOINTS** page. 
3. Click the ADD or DELETE button at the bottom of the page. Note that the default streaming endpoint cannot be deleted. 
4. Click the START button to start the streaming endpoint. 
5. Click on the name of the streaming endpoint to configure it.   

	![Origin page][origin-page]

##<a id="scale_streaming_endpoints"></a>Scale the Streaming Endpoint

Streaming units provide you with both dedicated egress capacity that can be purchased in increments of 200 Mbps and  additional functionality which currently includes [dynamic packaging capabilities](http://go.microsoft.com/fwlink/?LinkId=276874). By default, streaming is configured in a shared-instance model for which server resources (for example, compute, egress capacity, etc.) are shared with all other users. To improve a streaming throughput, it is recommended to purchase Streaming Units. 

To change the number of streaming units, do the following:

1. To specify the number of streaming units, select the SCALE tab and move the **reserved capacity** slider.

	![Scale page](./media/media-services-how-to-scale/media-services-origin-scale.png)

4. Press the SAVE button to save your changes.

	The allocation of any new streaming units takes around 20 minutes to complete. 

	 
	>[AZURE.NOTE] Currently, going from any positive value of streaming units back to none, can disable on-demand streaming for up to an hour.

	>[AZURE.NOTE] The highest number of units specified for the 24-hour period is used in calculating the cost. For information about pricing details, see [Media Services Pricing Details](http://go.microsoft.com/fwlink/?LinkId=275107).
	
##Configuring the Streaming Endpoint

The CONFIGURE tab enables you to perform configurations as shown in this image. The description of the fields follows.

>[AZURE.NOTE] The configuration on this page will only apply to streaming endpoints that have at least one reserved unit. To reserve the on-demand streaming reserved units.

![Configure origin][configure-origin]
  

1. Set the maximum caching period that will be specified in the cache control header of HTTP responses. This value will not override the maximum cache value that have been set explicitly on the blob content.

2. Specify IP addresses that would be allowed to connect to the published streaming endpoint. If no IP addresses specified, any IP address would be able to connect.

3. Specify configuration for Akamai signature header authentication.

4. You can specify a cross domain access policy for Adobe Flash clients (for more information see, [Cross-domain policy file specification](http://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html). As well as client access policy for Microsoft Silverlight clients (for more information, see [Making a Service Available Across Domain Boundaries](https://msdn.microsoft.com/en-us/library/cc197955(v=vs.95).aspx).  

5. You can also configure custom host names by Clicking the **configure** button. For more information, see the **CustomHostNames** property in the [StreamingEndpont](https://msdn.microsoft.com/en-us/library/dn783468.aspx) topic.  



[origin-page]: ./media/media-services-manage-origins/media-services-origins-page.png
[configure-origin]: ./media/media-services-manage-origins/media-services-origins-configure.png
[configure-origin-configure-custom-host-names]: ./media/media-services-manage-origins/media-services-configure-custom-host-names.png
