#OBD设备库存信息表OBD_Stock_Info；先备份obd_stock_info表
TRUNCATE TABLE obd2-test.obd_stock_info;
INSERT INTO obd2-test.obd_stock_info (
	stockId,
	obdId,
	obdSn,
	obdMSn,
	simNo,
	stockType,
	stockState,
	regUserId,
	startDate,
	gpsState,
	wifiState,
	hgDeviceSn,
	update_time,
	valid
) SELECT
	stockId,
	obdId,
	RIGHT (obdMSn, 8),
	obdSn,
	simNo,
	stockType,
	stockState,
	regUserId,
	startDate,
	gpsState,
	wifiState,
	hgDeviceSn,
	update_time,
	valid
FROM
	obd.obd_stock_info;

#用户表信息表（MEB_User）
INSERT INTO obd2-test.meb_user (
	regUserId,
	mobileNumber,
	obdSN,
	carId,
	license,
	NAME,
	sex,
	userType,
	PASSWORD,
	payPassword,
	valid,
	create_time,
	update_time
) SELECT
	regUserId,
	mobileNumber,
	obdSN,
	carId,
	license,
	NAME,
	sex,
	userType,
	PASSWORD,
	payPassword,
	valid,
	create_time,
	update_time
FROM
	obd.meb_user;

#2
UPDATE meb_user m,
 obd_stock_info o
SET m.obdSN = o.obdSn
WHERE
	m.obdSN = o.obdMSn;


#车型信息表（Car_Type）
INSERT INTO obd2-test.car_type 
SELECT
	*
FROM
	obd.car_type;

#车辆信息表（Car_info）
INSERT INTO obd2-test.car_info (
	carId,
	obdSN,
	license,
	carState,
	cartype_id,
	isfault,
	create_time,
	update_time,
	valid,
	regUserId
) SELECT
	carId,
	obdSN,
	license,
	carState,
	cartype_id,
	isfault,
	create_time,
	update_time,
	valid,
	regUserId
FROM
	obd.car_info;

#2
UPDATE car_info c,
 obd_stock_info o
SET c.obdSN = o.obdSn
WHERE
	c.obdSN = o.obdMSn;


#轨迹表（Car_GSPTrack）
INSERT INTO obd2-test.car_gsptrack (
	gspTrackId,
	obdSn,
	longitude,
	latitude,
	directionAngle,
	gpsSpeed,
	obdSpeed,
	high,
	gspTrackTime
) SELECT
	gspTrackId,
	RIGHT (obdSn, 8),
	longitude,
	latitude,
	directionAngle,
	gpsSpeed,
	obdSpeed,
	high,
	gspTrackTime
FROM
	obd.car_gsptrack;

#车辆行程记录表（Car_TravelTrack）
INSERT INTO obd2-test.car_traveltrack (
	id,
	obdsn,
	insesrtTime,
	travelEnd,
	travelNo,
	travelStart,
	distance,
	speed,
	-- overspeed,
	brakesNum,
	quickTurn,
	-- urgentBrakesNum,
	quickenNum,
	-- urgentquickenNum,
	quickSlowDown,
	quickLaneChange,
	-- averageSpeed,
	temperature,
	-- rotationalSpeed,
	engineMaxSpeed,
	speedMismatch,
	voltage,
	totalFuel,
	averageFuel,
	driverTime,
	message,
	overspeedTime,
	idling
) SELECT
	id,
	RIGHT (obdsn, 8),
	insesrtTime,
	travelEnd,
	travelNo,
	travelStart,
	distance,
	speed,
	-- overspeed,
	brakesNum,
	quickTurn,
	-- urgentBrakesNum,
	quickenNum,
	-- urgentquickenNum,
	quickSlowDown,
	quickLaneChange,
	-- averageSpeed,
	temperature,
	-- rotationalSpeed,
	rotationalSpeed,
	speedMismatch,
	voltage,
	totalFuel,
	averageFuel,
	driverTime,
	message,
	overspeedTime,
	idling
FROM
	obd.car_traveltrack;

#车辆油耗信息表（Car_Oil_Info）
TRUNCATE TABLE obd2-test.car_oil_info;
INSERT INTO obd2-test.car_oil_info (
	oilInfoId,
	carId,
	obdSN,
	petrolConsumeNum,
	mileageNum,
	timeSpanNum,
	oilInfoTime
) SELECT
	oilInfoId,
	carId,
	RIGHT (obdSN, 8),
	petrolConsumeNum,
	mileageNum,
	timeSpanNum,
	date_format(oilInfoTime, '%Y-%m-%d %T')
FROM
	obd.car_oil_info;


#驾驶行为表（car_drive_info）
INSERT INTO obd2-test.car_drive_info (
	driveInfoId,
	carId,
	obdSn,
	tmsSpeeding,
	tmsRapDec,
	tmsRapAcc,
	highSpeed,
	tmsSharpTurn,
	notMatch,
	longLowSpeed,
	tmsBrakes,
	tmsSteep,
	avSpeed,
	driveDate,
	tmsFatigue
) SELECT
	driveInfoId,
	carId,
	RIGHT (obdSn, 8),
	tmsSpeeding,
	tmsRapDec,
	tmsRapAcc,
	highSpeed,
	tmsSharpTurn,
	notMatch,
	longLowSpeed,
	tmsBrakes,
	tmsSteep,
	avSpeed,
	driveDate,
	tmsFatigue
FROM
	obd.car_drive_info;


#	故障上传信息表(fault_upload)
INSERT INTO obd2-test.fault_upload (
	fault_id,
	obdSn,
	fault_total,
	fault_code,
	create_time,
	update_time,
	state,
	remark
) SELECT
	fault_id,
	RIGHT (obdSn, 8) , 
	fault_total,
	fault_code,
	create_time,
	update_time,
	state,
	remark
FROM
	obd.fault_upload;

#字典表(dictionary)
INSERT INTO obd2-test.dictionary 
SELECT
	*
FROM
	obd.dictionary;

#	Obd当前版本 obd_curversion
TRUNCATE TABLE obd2-test.obd_curversion;

INSERT INTO obd2-test.obd_curversion (
	id,
	obdSn,
	hardware,
	iap,
	software,
	osoftware,
	create_time,
	update_time,
	remark
) SELECT
	id,
	RIGHT (obdSn, 8),
	hardware,
	iap,
	software,
	osoftware,
	create_time,
	update_time,
	remark
FROM
	obd.obd_curversion;


#位置信息表(Position_Info，新协议)
INSERT INTO obd2-test.position_info (
	id,
	obdSn,
	insertTime,
	statusGPS,
	type,
	timeType,
	time,
	longitude,
	latitude,
	longitudeType,
	latitudeType,
	directionAngle,
	gpsSpeed,
	obdSpeed,
	engineTemperature,
	satellites,
	satelliteStrength
) SELECT
	id,
	RIGHT (obdsn, 8),
	insesrtTime,
	statusGps,
	0,
	type,
	gpsTime,
	longitude,
	latitude,
	statusLongitude,
	statusLatitude,
	directionAngle,
	gpsSpeed,
	obdSpeed,
	engineTemperature,
	satellites,
	0
FROM
	obd.positional_information;


#位置-报警信息表(Position_Warn_Info，新协议)
INSERT INTO obd2-test.position_warn_info (
	id,
	positionInfoId,
	illegalStartUp,
	illegalShake,
	batteryLow,
	batteryUp,
	engineTemperature,
	vehicleFailure,
	overSpeed,
	elecFenceOut,
	elecFenceIn
) SELECT
	id,
	id,
	warnShock,
	warnCollision,
	warnBrown,
	warnOvervoltage,
	warnWaterTemperature,
	warnFailureSerious,
	warnOverspeed,
	warnOutRectangular,
	warnInRectangular
FROM
	obd.positional_information;