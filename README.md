# A Magento-centric Incident Response Plan Template

## Introduction 
This document provides you a structured process and sample procedures to use when responding to intrusions on our Magento eCommerce stores. Many parts of it has been lifted liberally from the MSDN documentation on Incident Response and adapted to needs of eCommerce systems.


## Prerequisites for using this document
*	Create an Incident Response Team (IRT) to deal with security incidents for each aspect of the eCommerce solution defined in the table below. This may be a small team with some roles overlapped within your company. You can use the table below as a starting point.

*	Routinely monitor and analyze network traffic and system performance.

*	Routinely check all logs and logging mechanisms, including operating system event logs, application specific logs and intrusion detection system logs. 

*	Verify your back-up and restore procedures. You should be aware of where backups are maintained, who can access them, and your procedures for data restoration and system recovery. Make sure that you regularly verify backups and media by selectively restoring data.



INCIDENT RESPONSE TEAM 

Role  | Name | Email | Phone  | IM  | Escalation Ladder  | Notes | 
------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
Incident Leader |||||||
Management/Stakeholder |||||||
IT Contact |||||||
Communications |||||||
Legal Representative |||||||
National/Local Law Enforcement |||||||
Hosting SLA contact |||||||
Magento EE SLA contact |||||||
3rd Party SaaS SLA contact  |||||||



## Definition of roles:

Role | Role Description |
------------- | ------------- |
Incident Lead | In the event of an incident, you should designate one individual responsible for coordinating the response. The  Incident Lead has ownership of the particular incident or set of related security incidents. All communication about the event is coordinated through the Incident Lead, and when speaking with those outside the IRT, he or she represents the entire IRT. The Incident Lead might vary depending on the nature of the incident, so feel free to have multiple versions of this document for each logical technical unit of your eCommerce system. |
IT Contact | This member is primarily responsible for coordinating communication between the Incident Lead and the rest of the IT group. The IT Contact might not have the particular technical expertise to respond to the particular incident; however, he or she will be primarily responsible for finding people in the IT group to handle particular security events. In smaller teams this may be the same person as the Incident Lead. |
Legal Representative  | This member is a lawyer who is very familiar with established incident response policies. The Legal Representative determines how to proceed during an incident with minimal legal liability and maximum ability to prosecute offenders.  Before an incident occurs, the Legal Representative should have input on monitoring and response policies to ensure that the organization is not being put at legal risk during a cleanup or containment operation. It is very important to consider the legal implications of shutting down a system and potentially violating service level agreements or membership agreements with your customers, or not shutting down a comprised system and being liable for damages caused by attacks launched from that system.  Any communication to outside law enforcement or external investigative agencies should also be coordinated with the Legal Representative. |
Communication/ Public Relations Officer  | Generally, this member is part of the public relations department and is responsible for protecting and promoting the image of the organization.  This individual might not be the actual face to the media and customers, but he or she is responsible for crafting the message (the content and objective of the message is generally the responsibility of management). All media inquiries should be directed to Public Relations. |
Management/Stakeholders | Depending on the particular incident, you might involve only departmental managers, or you might involve managers across the entire organization. The appropriate management individual will vary according to the impact, location, severity, and type of incident.  If you have a managerial point of contact, you can quickly identify the most appropriate individual for the specific circumstances. Management is responsible for approving and directing security policy.  Management is also responsible for determining the total impact (both financial and otherwise) of the incident on the organization. Management directs the Communications Officer regarding which information should be disclosed to the media and determines the level of interaction between the Legal Representative and law enforcement agencies. |
External resourses  | Include in the table above a list of all the contact information for all the services that are critical to your Magento eCommerce store. If you have an EE Licence, include all the information required to get into with Magento Support or ECG here. Add rows for your hosting provider support line, internal contacts and also even terms of service.  The goal here is that anything internal or external that affects the operation of your Magento eCommerce store should have a contact here. |


Responding to an Incident 

The following table shows the responsibilities of these individuals during the incident response process. 


Activity | Incident Lead | IT Contact | Legal Representative | Communications Officer | Management |
------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
Initial Assessment | Owner | Advises | None | None | None |
Initial Response | Owner | Implements | Updates | Updates | Updates |
Collects Forensic Evidence | Implements | Advises | Owner | None | None |
Implements Temporary Fix | Owner | Implements | Updates | Updates | Advises |
Sends Communication | Advises | Advises | Advises | Implements | Owner |
Check with Local Law Enforcement | Updates | Updates | Implements | Updates | Owner |
Implements Permanent Fix | Owner | Implements | Updates | Updates | Updates |
Determines Financial Impact on Business | Updates | Updates | Advises | Updates | Owner |
Review the response and update the plan | Implements | Advises | Advises | Advises | Advises |

## IMPLEMENTATION NOTES
 
#### Making an Initial Assessment
*	You should confirm whether you are dealing with an actual incident or a false positive. 

*	Gain a general idea of the type and severity of attack. You should gather at least enough information to begin communicating it for further research and to begin containing the damage and minimizing the risk. 

*	IMPORTANT: Record your actions thoroughly. These records will later be used for documenting the incident (whether actual or false). 

Note: You should avoid false positives whenever possible; however, it is always better to act on a false positive than fail to act on a genuine incident. Your initial assessment should, therefore, be as brief as possible, yet still eliminate obvious false positives. 

#### Communicating the Incident
Be aware that damage can come in many forms, and that a headline in the popular sites exaggerating a security breach can be much more destructive than an actual intrusions. For this reason, and to prevent an attacker from being tipped off, only those playing a role in the incident response should be informed until the incident is properly controlled. Based on the unique situation, your team will later determine who needs to be informed of the incident. This could be anyone from specific individuals up to the entire company and external customers. Communication externally should be coordinated with the Legal Representative.

#### Containing the Damage and Minimizing the Risks

*	Protect classified and sensitive data. As part of your planning for incident response, you should already have a clear definition of which data is classified and which is sensitive. This will enable you to prioritize your responses in protecting all customer card data, and identifiable customer information. With Magento this is mostly stored in the MySQL database but also be aware of the possibility of Varnish, Apache or PHP logs being dumped to disk.  

* 	Minimize disruption of computing resources (including processes). Although uptime is very important in most Magento stores, keeping them up during an attack might result in greater problems later on. Compare the cost of taking the compromised and related systems offline against the risk of continuing operations. In the vast majority of cases, you should immediately take the system off the network. However, you might have service agreements in place that require keeping systems available even with the possibility of further damage occurring. Under these circumstances, you can choose to keep a system online with limited connectivity in order to gather additional evidence during an ongoing attack. 


#### Identifying the Severity of the Compromise
*	Determine the intent of the attack. Was the attack specifically directed at your store or was it random? 

*	Identify the systems that have been compromised, only App servers? Was the database compromised?  


#### Preserving forensic evidence
*	In some cases, the benefit of preserving data might not equal the cost of delaying the response and recovery of the system. The costs and benefits of preserving data should be compared to those of faster recovery for each event.
*	For extremely large stores, comprehensive backups of all compromised systems and databases might not be feasible. Instead, you should back up all logs and selected, breached portions of the system.


#### External notifications
*	For higher profile companies and incidents, the media might be involved. Media attention to a security incident is rarely desirable, but it is often unavoidable. Media attention can enable your organization to take a proactive stance in communicating the incident. At a minimum, the incident response procedures should clearly define the individuals authorized to speak to media representatives.
*	You should not attempt to deny to the media that an incident has occurred, because doing so is likely to damage your reputation more than proactive admission and visible responses ever will. This does not mean that you need to notify the media for each and every incident regardless of its nature or severity. You should assess the appropriate media response on a case-by-case basis.


#### Compiling and Organizing Incident Evidence

*	The CSIRT should thoroughly document all processes when dealing with any incident. This should include a description of the breach and details of each action taken (who took the action, when they took it, and the reasoning behind it). All people involved with access must be noted throughout the response process.
*	Afterward, the documentation should be chronologically organized, checked for completeness, and signed and reviewed with management and legal representatives. You will also need to safeguard the evidence collected in the protect evidence phase. You should consider having two people present during all phases who can sign off on each step. This will help reduce the likelihood of evidence being inadmissible and the possibility of evidence being modified afterward.
*	Remember that the offender might be an employee, contractor, temporary employee, or other insider within your organization. Without thorough, detailed documentation, identifying an inside offender will be very difficult. Proper documentation also gives you the best chance of prosecuting offenders.



## Important Considerations for implementation

After you have completed this document for your team, it is highly advised that you undergo drills to see how your team uses it and responds to issues. This way you can identify shortcomings or extra information you can add to it.

These steps are not purely sequential. Rather, they happen throughout the incident. For example, documentation starts at the very beginning and continues throughout the entire life cycle of the incident; communication also happens throughout the entire incident. 

An overzealous response could even cause more damage than the initial attack. By working these steps alongside each other, you will get the best compromise between swift and effective action. It is very important that you thoroughly test your incident response process before an incident occurs. Without thorough testing, you cannot be confident that the measures that you have in place will be effective in responding to incidents. 


## Related Information
For more information about creating an incidence response plan, see the following: 
*	[Handbook for Computer Security Incident Response Teams](http://go.microsoft.com/fwlink/?LinkId=22398)
*	Incident Response: Investigating Computer Crime by Chris Prosise and Kevin Mandia (McGraw-Hill Professional Publishing, ISBN: 00723829). 



